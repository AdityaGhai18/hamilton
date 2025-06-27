# hamilton

1. Create a Python virtual environment `python3 -m venv venv`
2. Run `pip install -r requirements.txt`
3. Run the backend by cd-ing into the backend directory and run `python3 server.py`

Before you push your code, just run `pip freeze > requirements.txt`

⚙️ what it does
hamilton is a multi-agent AI platform that simulates the dynamics of an actual senate committee hearing to lower the barrier to entry to the political sphere in an approachable manner. With real-time audio conversations between our senator agents, you can follow along with what bills and clauses senators are actively discussing and visualize the active changes they are making as they debate the outcomes and impacts of these bills. It enables you to learn about the process to go from a bill proposal to the final majority-approved outcome.

demo: https://vimeo.com/1021472373

⛏️ how we built it: our process
Given the inherent complexity of our project, we spent a significant amount of our early time building a rock solid system infrastructure plan before touching any code. We narrowed down the sponsors that would best enable us to fulfill our vision, and laid out the data access objects, the communication channels between processes, and our tech stack. Below is a higher-level overview of our system design:

We then split up our project into sections that could be tested individually to then eventually integrate into the full system. In particular, we broke up the frontend UI and event handling, the REST and WebSocket-based backends for delivering bill outputs to the frontend, and an independent multi-agent system based on AutoGen. The latter required significant data collection for personalized Senator agents through various media sources. To parse and retrieve this data during runtime, we were able to set up a ChromaDB database for vectorized search quickly. This allowed us to provide the correct personality and historical context for each senator agent in relation to the user-submitted bill. For the Next.js frontend, we really loved using Cartesia’s fast and easy API for speech generation. Just using brief voice recordings of each senator, we were able to create expressive, emotional voice clones that we had a blast experimenting with. We envision adding more senators to our platform, which is easily possible with Cartesia’s voice cloning capabilities. To effectively track the evolving bills within Hamilton, we utilize Git version control. This approach enables us to maintain a comprehensive record of all changes, ensuring that each senator’s contributions are clearly documented. The version control system enhances transparency and provides deeper insights into this political process. This way, we can easily review the modifications made during discussions, allowing for a clearer understanding of the dynamics at play in the simulated senate committee hearings.
