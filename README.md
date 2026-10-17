# Job Helper Agent Design Patterns

Two Python notebooks exploring ReAct and ReWOO workflows for comparing CV information with job-posting requirements.

## Approaches

- [ReAct Agent](ReAct%20Agent.ipynb): a LangGraph tool-calling loop with CV extraction, job-posting lookup, and an in-memory checkpointer.
- [ReWOO Agent](ReWOO%20Agent.ipynb): separate planning, tool execution, and answer-generation stages using evidence references.

Both examples use OpenAI model calls through the OpenAI SDK and LangChain. They are experiments, not a benchmark demonstrating that one approach is more effective.

## Inputs and dependencies

The notebooks import LangChain, LangGraph, LangSmith, python-dotenv, python-docx, and pdfplumber alongside the OpenAI SDK. Legacy `.doc` conversion additionally calls LibreOffice's `soffice` command.

There is no dependency manifest in the repository. Establish a compatible isolated environment and review the notebooks before execution. Supply `OPENAI_API_KEY` through local environment configuration, never through committed source.

## Known limitations

- The ReWOO solver references an undefined `solver_promp` name and uses a formatting keyword inconsistent with the declared template. That cell needs correction before the complete flow can run.
- Example CV paths and job links are local/historical examples, not portable fixtures.
- API/model availability and end-to-end behavior have not been verified.
- Model-generated comparisons require human review and may contain errors.

## Privacy

CV contents and job information may be sent to the configured model provider, and configured tracing can capture workflow data. Use synthetic CVs for demos and inspect retained notebook outputs before sharing. Do not run against private documents without reviewing the data flow.

