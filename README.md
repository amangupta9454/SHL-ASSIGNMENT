<div align="center" style="font-family: 'Inter', sans-serif; max-width: 900px; margin: 0 auto; padding: 20px;">
  
  <div style="background: linear-gradient(135deg, #020617, #0f172a, #1e293b); padding: 60px 40px; border-radius: 24px; box-shadow: 0 25px 50px -12px rgba(0,0,0,0.5); color: white; border: 1px solid rgba(255,255,255,0.1);">
    <div style="display: inline-block; padding: 8px 16px; background: rgba(16, 185, 129, 0.15); border: 1px solid rgba(16, 185, 129, 0.3); border-radius: 30px; color: #34d399; font-weight: 600; font-size: 0.85rem; letter-spacing: 1px; margin-bottom: 20px; text-transform: uppercase;">SHL Labs Take-Home Assignment</div>
    <h1 style="font-size: 3.5rem; margin-bottom: 15px; font-weight: 900; background: -webkit-linear-gradient(#38bdf8, #818cf8); -webkit-background-clip: text; -webkit-text-fill-color: transparent; letter-spacing: -1.5px;">Assessment Recommender</h1>
    <h3 style="color: #cbd5e1; font-weight: 400; font-size: 1.25rem; margin-top: 0; max-width: 600px; margin: 0 auto; line-height: 1.6;">An intelligent, conversational AI consultant powered by Google Gemini 3.0 Flash Preview.</h3>
    
    <div style="margin-top: 35px; display: flex; gap: 15px; justify-content: center; flex-wrap: wrap;">
      <span style="background: rgba(255, 255, 255, 0.05); color: #e2e8f0; padding: 8px 16px; border-radius: 12px; font-size: 0.9rem; font-weight: 500; border: 1px solid rgba(255, 255, 255, 0.1); display: flex; align-items: center; gap: 8px;">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
        FastAPI
      </span>
      <span style="background: rgba(255, 255, 255, 0.05); color: #e2e8f0; padding: 8px 16px; border-radius: 12px; font-size: 0.9rem; font-weight: 500; border: 1px solid rgba(255, 255, 255, 0.1); display: flex; align-items: center; gap: 8px;">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#fcd34d" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="16" x2="12" y2="12"/><line x1="12" y1="8" x2="12.01" y2="8"/></svg>
        Gemini 3.0 Flash
      </span>
      <span style="background: rgba(255, 255, 255, 0.05); color: #e2e8f0; padding: 8px 16px; border-radius: 12px; font-size: 0.9rem; font-weight: 500; border: 1px solid rgba(255, 255, 255, 0.1); display: flex; align-items: center; gap: 8px;">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#f472b6" stroke-width="2"><path d="M18 3a3 3 0 0 0-3 3v12a3 3 0 0 0 3 3 3 3 0 0 0 3-3 3 3 0 0 0-3-3H6a3 3 0 0 0-3 3 3 3 0 0 0 3 3 3 3 0 0 0 3-3V6a3 3 0 0 0-3-3 3 3 0 0 0-3 3 3 3 0 0 0 3 3h12a3 3 0 0 0 3-3 3 3 0 0 0-3-3z"/></svg>
        Vanilla JS
      </span>
    </div>
  </div>

  <p style="text-align: left; font-size: 1.15rem; line-height: 1.8; color: #334155; margin: 40px 0; padding: 0 10px;">
    The SHL Assessment Recommender is a full-stack web application designed to help recruiters and hiring managers seamlessly discover the perfect talent assessment. By leveraging the immense context window of Gemini 3.0 Flash Preview, the agent natively understands a catalog of over 10,000 assessments without the need for complex Retrieval-Augmented Generation (RAG) pipelines.
  </p>

  <hr style="border: 0; height: 1px; background: linear-gradient(to right, transparent, #cbd5e1, transparent); margin: 50px 0;">

  <div style="text-align: left; background: #ffffff; padding: 40px; border-radius: 24px; border: 1px solid #e2e8f0; box-shadow: 0 10px 30px rgba(0,0,0,0.02);">
    <h2 style="color: #0f172a; font-size: 2rem; margin-top: 0; display: flex; align-items: center; gap: 12px; margin-bottom: 25px;">
      <span style="background: #10b981; color: white; border-radius: 12px; width: 40px; height: 40px; display: inline-flex; align-items: center; justify-content: center; font-size: 1.2rem; box-shadow: 0 4px 10px rgba(16, 185, 129, 0.3);">🚀</span>
      Quick Start Guide
    </h2>
    
    <div style="margin-top: 30px;">
      <h4 style="color: #334155; margin-bottom: 12px; font-size: 1.1rem; display: flex; align-items: center; gap: 8px;">
        <span style="background: #f1f5f9; padding: 4px 10px; border-radius: 8px; font-size: 0.9rem; color: #64748b;">01</span> 
        Install Dependencies
      </h4>
      <pre style="background: #0f172a; color: #e2e8f0; padding: 20px; border-radius: 12px; overflow-x: auto; font-family: 'JetBrains Mono', monospace; font-size: 0.95rem; border: 1px solid #1e293b; box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);">cd backend
pip install -r requirements.txt</pre>
    </div>

    <div style="margin-top: 30px;">
      <h4 style="color: #334155; margin-bottom: 12px; font-size: 1.1rem; display: flex; align-items: center; gap: 8px;">
        <span style="background: #f1f5f9; padding: 4px 10px; border-radius: 8px; font-size: 0.9rem; color: #64748b;">02</span> 
        Configure Environment
      </h4>
      <p style="color: #64748b; font-size: 0.95rem; margin-bottom: 10px;">Create a <code>.env</code> file in the root directory and add your Google Gemini API key.</p>
      <pre style="background: #0f172a; color: #e2e8f0; padding: 20px; border-radius: 12px; overflow-x: auto; font-family: 'JetBrains Mono', monospace; font-size: 0.95rem; border: 1px solid #1e293b; box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);">GEMINI_API_KEY=AIzaSyYourKeyHere...</pre>
    </div>

    <div style="margin-top: 30px;">
      <h4 style="color: #334155; margin-bottom: 12px; font-size: 1.1rem; display: flex; align-items: center; gap: 8px;">
        <span style="background: #f1f5f9; padding: 4px 10px; border-radius: 8px; font-size: 0.9rem; color: #64748b;">03</span> 
        Launch Application
      </h4>
      <pre style="background: #0f172a; color: #e2e8f0; padding: 20px; border-radius: 12px; overflow-x: auto; font-family: 'JetBrains Mono', monospace; font-size: 0.95rem; border: 1px solid #1e293b; box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);">cd backend
uvicorn main:app --reload --port 8000</pre>
    </div>

    <div style="margin-top: 30px; background: #f8fafc; padding: 20px; border-radius: 12px; border-left: 4px solid #38bdf8;">
      <h4 style="color: #0f172a; margin-bottom: 5px; font-size: 1.1rem;">🎉 Ready to use!</h4>
      <p style="color: #475569; margin-top: 5px; line-height: 1.5;">The frontend is statically served by FastAPI. Simply navigate to <strong><a href="http://127.0.0.1:8000/" style="color: #0ea5e9; text-decoration: none; font-weight: 600;">http://127.0.0.1:8000/</a></strong> in any modern web browser to interact with the agent.</p>
    </div>
  </div>

  <div style="text-align: left; margin-top: 60px;">
    <h2 style="color: #0f172a; font-size: 2rem; display: flex; align-items: center; gap: 12px; margin-bottom: 25px;">
      <span style="background: #6366f1; color: white; border-radius: 12px; width: 40px; height: 40px; display: inline-flex; align-items: center; justify-content: center; font-size: 1.2rem; box-shadow: 0 4px 10px rgba(99, 102, 241, 0.3);">⚡</span>
      Core Capabilities
    </h2>
    
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin-top: 20px;">
      <div style="background: #ffffff; padding: 25px; border-radius: 16px; border: 1px solid #e2e8f0; box-shadow: 0 4px 6px rgba(0,0,0,0.02);">
        <h3 style="color: #1e293b; font-size: 1.2rem; margin-top: 0; margin-bottom: 10px;">Zero-RAG Retrieval</h3>
        <p style="color: #64748b; font-size: 0.95rem; line-height: 1.6;">Leverages Gemini's massive context window to parse all 10,000+ JSON catalog entries natively without vector database latency.</p>
      </div>
      
      <div style="background: #ffffff; padding: 25px; border-radius: 16px; border: 1px solid #e2e8f0; box-shadow: 0 4px 6px rgba(0,0,0,0.02);">
        <h3 style="color: #1e293b; font-size: 1.2rem; margin-top: 0; margin-bottom: 10px;">URL Integrity</h3>
        <p style="color: #64748b; font-size: 0.95rem; line-height: 1.6;">Backend firewall actively prevents LLM hallucination by replacing generated links with the exact, literal <code>link</code> field from the catalog.</p>
      </div>

      <div style="background: #ffffff; padding: 25px; border-radius: 16px; border: 1px solid #e2e8f0; box-shadow: 0 4px 6px rgba(0,0,0,0.02);">
        <h3 style="color: #1e293b; font-size: 1.2rem; margin-top: 0; margin-bottom: 10px;">Stateless Execution</h3>
        <p style="color: #64748b; font-size: 0.95rem; line-height: 1.6;">FastAPI server holds no conversational state. The entire conversation JSON tree is passed dynamically via DOM management.</p>
      </div>

      <div style="background: #ffffff; padding: 25px; border-radius: 16px; border: 1px solid #e2e8f0; box-shadow: 0 4px 6px rgba(0,0,0,0.02);">
        <h3 style="color: #1e293b; font-size: 1.2rem; margin-top: 0; margin-bottom: 10px;">Cost Guardrails</h3>
        <p style="color: #64748b; font-size: 0.95rem; line-height: 1.6;">Hardcoded 8-turn (16 message) termination logic prevents prompt looping, infinite injection attacks, and API abuse.</p>
      </div>
    </div>
  </div>

</div>
