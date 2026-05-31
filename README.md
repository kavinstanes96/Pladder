# Pladder
Multi agent coding generator and orchestrator with strongly strongly typed contract for sub agents.

A rust application design plan (could be low level design plan LLD or high level) will be designed and submitted to supervisor agent. 

One supervisor Agent (has access to central plan)
One evaluator agent (has access to central plan)

Access to central plan implies the agent (supervisor & evaluator only) sees the whole big picture.

You have a generated plan with LLD. → Supervisor Takes LLD , generates input and output contract for sub agent → supervisor spins up sub-agent, each sub-agent will implement a crate with one or more modules → evaluator (run test unit & integration).

evaluator good → de-queue work item from central plan
evaluator not good → give feedback to planner + existing items.

Upon queue empty, supervisor will put them together.

In LangGraph, a "Node" is simply a Python function. There is no rule that says a LangGraph node has to be a standard LangChain agent. You can actually wrap a specific MetaGPT Role inside a LangGraph node.  

    The Node: You create a LangGraph node called generate_contract. Inside that Python function, you instantiate a MetaGPT Architect role.

    The Flow: The LangGraph Supervisor says, "I need a design for the Database Crate." It routes to the generate_contract node. The MetaGPT Architect takes over, generates a strictly defined contract using its internal SOPs, and returns it to the LangGraph state.

    The Benefit: You can utilize MetaGPT's high-quality, specialized prompts for specific tasks without having to adopt its entire start-to-finish pipeline.
