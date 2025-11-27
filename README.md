Readme
read_file_tool(state):
Reads a text file from state["filepath"] using UTF‑8.
Returns {"results": file_text, "confidence": 0.95} on success; logs and returns empty results with 0.0 on error.
Needs logger and Path imported.
decide_if_clarify(state):
Routes workflow: returns "clarify" if confidence < CONFIDENCE_THRESHOLD else "summarize".
Needs CONFIDENCE_THRESHOLD and logger defined.
ask_user_tool(state):
Prompts the user for clarification using state["clarify_question"].
Returns {"clarification": "..."}.
Raises if empty input. Uses logger.
llm_summarize_tool(state):
Sends state["results"] to an LLM and returns {"final_summary": summary}.
Runs the pipeline: read -> route -> optional clarify -> summarize -> save -> print final state.
 
