## 2026-05-12 - Initial Creation

**Decided to build a fictional company instead of another case study.**

Context: Had finished two ransomware case studies (NHS WannaCry, AGCO) and was looking for the next one. Considered another NIST, another ISO, a breach, or postmortem but felt the single document format was sort of limited.

Decision: Build a fictional company that produces an ongoing set of GRC artifacts, not another isolated case study about something that already happened.

Rationale: Saw someone on GitHub earlier this year who had made a fake company with a couple of markdown files and screenshotted for later Git projects. The idea stuck because a fictional company feels creative and removes the constraint of writing about a real public incident. Since the company is mine to define the postmortems, policies, risk registers, etc. can be whatever I want them to be.

Consequences: I'm now committed to maintaining one larger project over time. Higher upfront work too but more total artifacts at the end and a cleaner narrative.

---

**Decided to build the company website too, not just the GitHub repo.**

Context: With the fictional company decided, the next question was whether to make it purely a documentation project or build a public-facing site for it as well.

Decision: Build the actual website at fenn.wichman.io alongside GRC docs.

Rationale: I'm playing tech catch up at basically every angle including GitHub, terminal, dev environments, subdomains, and web frameworks. Building the website forces me to learn the technical side. A repo only project would have been easier but wouldn't have exercised the same range of skills.

Consequences: Project scope more than doubles. I'm now responsible for design decisions, learning Astro, GitHub Pages deployment and DNS configuration again. Not my first time with GitHub Pages or DNS (I have a portfolio site and two domains) or terminal (CompTIA A+) but far from a mastermind. The resulting portfolio piece is more dynamic (writing + design + technical) instead of just a document.

---

**Picked agritech as the industry.**

Context: Needed to choose an industry for the fictional company. Considered a coffee shop or vintage store.

Decision: Agritech.

Rationale: SaaS and GRC are unfamiliar enough to me on their own so reducing one variable by choosing ag lets me prioritize learning the skills and not learning a whole industry. Briefly worried picking agritech would make me look farm-obsessed (I slightly am) or like I only want to work in agritech (I do not). Pushed through the doubt because the skills practice/showcase felt worth the perception risk.

Consequences: I can speak at length about the industry, fictional company's product, customers, regulations, etc. Slight risk that reviewers read this as a niche/pigeonhole instead of a deliberate choice. This needs to be framed clearly in the project essay.

---

**Picked the name Furrow.**

Context: Needed a name for the company. Wanted something in the realm of land, countryside, plants, green.

Decision: Started with Furrow. Set up the GitHub Pages repo, wrote the README, configured the basics.

Rationale: Liked the name. Tied to farming, evocative, short.

Consequences: Didn't yet know enough about UK trademark law or Companies House registration to do thorough checks. Furrow would need to be revisited.

---

**Wrote the company brief.**

Context: Needed a foundational document that establishes who the fictional company is, what it does, who its customers are, and what regulatory environment it operates in. Every other artifact would reference back to this.

Decision: Had fun writing a full company brief covering the overview, founder's story and their "why", product, customers, technology stack, vendors, regulatory posture, and current state.

Rationale: Impossible to write any type of documentation without knowing what 
the company actually does. Also set up the brief with intentional specifics 
that would open the door for future docs; for example, a sub-processor breach 
makes an incident response plan natural to write, an ISO 27001 audit in progress 
makes audit prep docs natural. Wanted Fenn to specifically be privacy-focused 
(customer-held keys, no surveillance default, "Your land. Your data. Your 
decision." tagline) because that's the product I wish actually existed in 
agritech and it gives the GRC work a distinct point of view rather than 
just generic SaaS compliance.

Consequences: Locked in foundational facts (UK-based, Bristol, ~1,000 farms, Series B, ~100 employees, AWS London, Proton internal tooling, ICO as regulator). Some of these facts would need to be revisited later when I realized parts of the brief had legal issues (covered in Thursday's entry).

---

**Designed the site roughly.**

Context: Needed a working visual direction before starting to build in Astro.

Decision: Sketched out the landing page structure, branding (colors, typography), and sections.

Rationale: Easier to build the site when I already know what it should look 
like. Astro is unfamiliar enough on its own; figuring out design while learning 
the framework would slow both down.

Consequences: Had a working visual direction to build from. Decisions about hero, nav structure, sections, and brand identity are easy tweaks to get right when I can see it.

---

**Downloaded Astro and set up the dev environment.**

Context: Decided earlier to build the site in Astro for GitHub Pages deployment.

Decision: Downloaded Astro, set up SSH key for GitHub auth, scaffolded the site locally.

Rationale: Need the dev environment set up before I can start actually building pages. Better to get this out of the way early than hit setup friction mid-design.

Consequences: Local dev environment is ready. Next time I sit down to build, I can start building immediately.
