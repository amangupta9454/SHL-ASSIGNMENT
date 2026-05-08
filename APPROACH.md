<div align="center" style="font-family: 'Inter', sans-serif; max-width: 900px; margin: 0 auto; padding: 20px;">
  <div style="background: linear-gradient(135deg, #1e293b, #0f172a, #000000); padding: 50px 40px; border-radius: 20px; box-shadow: 0 20px 40px rgba(0,0,0,0.4); color: white; margin-bottom: 40px; text-align: center;">
    <h1 style="font-size: 3rem; margin-bottom: 15px; font-weight: 800; letter-spacing: -1px; background: -webkit-linear-gradient(#4FC3F7, #f8fafc); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">Architectural Approach</h1>
    <h3 style="color: #94a3b8; font-weight: 400; font-size: 1.2rem; margin-top: 0;">Deep Analysis & Design Decisions for the SHL Assessment Recommender</h3>
  </div>
  <div style="text-align: left; background: white; padding: 40px; border-radius: 20px; border: 1px solid #e2e8f0; box-shadow: 0 10px 25px rgba(0,0,0,0.03); margin-bottom: 30px;">
    <h2 style="color: #0f172a; font-size: 1.8rem; margin-top: 0; display: flex; align-items: center; gap: 15px; border-bottom: 2px solid #f1f5f9; padding-bottom: 15px;">
      <span style="font-size: 1.6rem;">🧠</span> 1. The LLM Backbone: Google Gemini 3.0 Flash Preview
    </h2>
    <p style="color: #475569; line-height: 1.8; font-size: 1.1rem; margin-top: 20px;">
      The original implementation utilized Anthropic's Claude 3.5 Sonnet. Through rigorous analysis of latency, cost, and context-window requirements, the decision was made to strategically migrate to <strong>Google Gemini 3.0 Flash Preview</strong> utilizing the official <code>google-genai</code> Python SDK.
    </p>
    <h4 style="color: #1e293b; font-size: 1.2rem; margin-top: 25px; margin-bottom: 10px;">Why Gemini Flash over RAG?</h4>
    <p style="color: #475569; line-height: 1.8; font-size: 1.05rem;">
      Traditional recommendation chatbots employ Retrieval-Augmented Generation (RAG) by chunking catalogs into vector databases (e.g., Pinecone, Chroma) and performing cosine-similarity searches. However, our newly scraped `catalog.json` contains over 10,000 highly specific assessment variants. 
    </p>
    <p style="color: #475569; line-height: 1.8; font-size: 1.05rem; margin-top: 10px;">
      Gemini Flash boasts a multi-million token context window with near-instantaneous processing capabilities. By natively injecting the <em>entire JSON catalog</em> directly into the System Prompt (via the <code>CATALOG_TEXT</code> string builder in <code>main.py</code>), we achieve <strong>Zero-RAG architecture</strong>. This eliminates the latency of vector similarity searches, solves the "lost in the middle" retrieval problem, and ensures the LLM has global, perfect context of every SHL assessment simultaneously.
    </p>
  </div>
  <div style="text-align: left; background: white; padding: 40px; border-radius: 20px; border: 1px solid #e2e8f0; box-shadow: 0 10px 25px rgba(0,0,0,0.03); margin-bottom: 30px;">
    <h2 style="color: #0f172a; font-size: 1.8rem; margin-top: 0; display: flex; align-items: center; gap: 15px; border-bottom: 2px solid #f1f5f9; padding-bottom: 15px;">
      <span style="font-size: 1.6rem;">🏗️</span> 2. Backend Architecture: FastAPI & Stateless Enforcement
    </h2>
    <p style="color: #475569; line-height: 1.8; font-size: 1.1rem; margin-top: 20px;">
      The backend is powered by <strong>FastAPI</strong>, a modern, high-performance web framework.
    </p>
    <ul style="color: #475569; line-height: 1.8; font-size: 1.05rem; margin-top: 15px; padding-left: 20px;">
      <li><strong style="color: #1e293b;">Stateless API Design:</strong> The <code>/chat</code> endpoint holds absolutely no memory in the server memory space. The entire conversation history is managed securely in the client's DOM and passed dynamically as a JSON payload in the request body. This prevents server-side memory leaks and allows for infinite horizontal scaling.</li>
      <li><strong style="color: #1e293b;">Anti-Hallucination Pipeline (Post-Processing):</strong> Even the best LLMs hallucinate URLs. The <code>parse_agent_response</code> function in <code>main.py</code> acts as an iron-clad firewall. When Gemini returns a list of recommended assessments, the backend intercepts it, discards the LLM-generated URLs, and cross-references the assessment name against the loaded <code>CATALOG_BY_NAME</code> dictionary. It then forcefully injects the literal, valid <code>link</code> field from <code>catalog.json</code> into the payload before sending it to the user. Broken 404 links are mathematically impossible.</li>
      <li><strong style="color: #1e293b;">Environment Variable Security:</strong> Sensitive credentials like <code>GEMINI_API_KEY</code> are loaded via <code>python-dotenv</code> outside of the application's source tree, adhering to Twelve-Factor App methodologies.</li>
    </ul>
  </div>
  <div style="text-align: left; background: white; padding: 40px; border-radius: 20px; border: 1px solid #e2e8f0; box-shadow: 0 10px 25px rgba(0,0,0,0.03); margin-bottom: 30px;">
    <h2 style="color: #0f172a; font-size: 1.8rem; margin-top: 0; display: flex; align-items: center; gap: 15px; border-bottom: 2px solid #f1f5f9; padding-bottom: 15px;">
      <span style="font-size: 1.6rem;">🎨</span> 3. Frontend Architecture: Vanilla JS & Responsive CSS
    </h2>
    <p style="color: #475569; line-height: 1.8; font-size: 1.1rem; margin-top: 20px;">
      The client interface (<code>frontend/index.html</code>) was built using pure Vanilla JavaScript, HTML, and highly customized CSS, avoiding the bloat of heavy frameworks like React or Angular for a single-page chat application.
    </p>
    <ul style="color: #475569; line-height: 1.8; font-size: 1.05rem; margin-top: 15px; padding-left: 20px;">
      <li><strong style="color: #1e293b;">Premium UI/UX:</strong> The interface features a deeply custom aesthetic, including SVG noise overlays for texture, CSS variables for centralized theme management, and smooth <code>@keyframes slideUp</code> micro-animations for message pop-ins.</li>
      <li><strong style="color: #1e293b;">Dynamic DOM Manipulation:</strong> Recommendations are rendered dynamically into a dedicated sidebar using the <code>renderRecommendations</code> function. It handles edge cases, empty states, and dynamic typography sizing natively.</li>
      <li><strong style="color: #1e293b;">Client-Side State Guardrails:</strong> The frontend actively tracks the "Turn Counter". Upon reaching 8 turns (16 total messages), the input area gracefully locks down to prevent infinite loops and runaway API costs.</li>
    </ul>
  </div>
  <div style="text-align: left; background: #f0fdf4; padding: 40px; border-radius: 20px; border: 1px solid #bbf7d0; box-shadow: 0 10px 25px rgba(0,0,0,0.03);">
    <h2 style="color: #166534; font-size: 1.8rem; margin-top: 0; display: flex; align-items: center; gap: 15px; border-bottom: 2px solid #dcfce7; padding-bottom: 15px;">
      <span style="font-size: 1.6rem;">🛡️</span> 4. System Prompt Engineering
    </h2>
    <p style="color: #15803d; line-height: 1.8; font-size: 1.1rem; margin-top: 20px;">
      The core intelligence of the agent is driven by a highly structured System Prompt.
    </p>
    <ul style="color: #15803d; line-height: 1.8; font-size: 1.05rem; margin-top: 15px; padding-left: 20px;">
      <li><strong>Behavioral Guidelines:</strong> The agent is explicitly instructed to CLARIFY, RECOMMEND, REFINE, COMPARE, and REFUSE. This creates a predictable conversational flow where the agent acts as a consultant rather than a generic search engine.</li>
      <li><strong>Strict JSON Enforcement:</strong> Gemini is forced to output responses matching a Pydantic-like schema (<code>{"reply": "...", "recommendations": [], "end_of_conversation": false}</code>). This allows the frontend to parse the structural data perfectly every time.</li>
      <li><strong>Out-of-Bound Refusals:</strong> The prompt aggressively denies prompt injections, salary benchmarking, and general hiring advice, restricting the scope strictly to the SHL product line.</li>
    </ul>
  </div>

</div>
