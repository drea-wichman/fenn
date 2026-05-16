## 2026-05-15: Starting the build log

**Started the build log and picked an ADR-influenced format for it.**

Context: After 3 days of building Fenn realized I'd been doing a lot of work across a lot of different surfaces: terminal, git, Astro, trademark and Companies House research, GRC documentation, decisions about what's public-facing vs internal, design, legal framing. Plus the mistakes I made along the way, messy but it's all been real work. All of that would normally just live and die in private and I didn't want it to go to waste. Future employers and future me get a real look at the range of work and the thought processes behind each decision.

Decision: Picked an ADR-influenced format with four fields per decision: Context, Decision, Rationale, Consequences. Not strictly any one template, but closest to Nygard's original with Merson's "Rationale" field added. Built out Tuesday, Wednesday, and Thursday entries.

Rationale: ADRs are a real convention in engineering, GRC, and architecture work. Auditors recognize the pattern. ISO 27001 and SOC 2 assessments look for evidence that decisions were made with context and reasoning. Using the format signals I understand how mature teams document.

Researched the main ADR templates:
- **Nygard (2011)** - foundational template, most widely adopted. Four fields: Title, Status, Context, Decision, Consequences. Reasoning is inside Context.
- **MADR** - adds "Decision Drivers" and "Considered Options." Better for team decisions with multiple alternatives.
- **Y-Statements** - single sentence template. Too compressed for a log.
- **Merson** - Nygard plus an explicit Rationale field. Easier to write.
- **Tyree-Ackerman** - enterprise template with many fields. Overkill.
- **Alexandrian** - pattern-language style. Seems to be used more in software architecture writing.

Consequences: Build log will use Context/Decision/Rationale/Consequences for decision bullets and plain prose. Each entry gets a date heading and a short title. Reverse chronological order. One file at the root of the fenn repo. If the log gets too long later I can change it to individual ADR files in a /decisions/ folder.

---

## 2026-05-14: More Legal Cleanup

**Legal paranoia audit: caught everything else I'd been claiming that I shouldn't.**

Context: After the Furrow, Fellow, Fenn name disaster I was paranoid. If I'd been wrong about names for two days, what else was I wrong about? Did a full audit of every credential, partnership, certification, and trademark reference across the company brief and site mockups.

Decision: Found and fixed six separate issues:
- **B Corp claim**, removed
- **Agri-TechE membership**, removed
- **Waitrose Farming for Nature partnership**, removed
- **BSI named as ISO 27001 certifier**, removed
- **"Fenn Agritech Ltd."** changed to "Fenn Agritech" (Ltd. is a regulated UK suffix)
- **"Farmers First" tagline** changed to "Your land. Your data. Your decision." (Farmers First was taken)

Rationale: Each individual claim was small but the pattern was the problem. Every one of these was a credential or affiliation I didn't have the right to use. "Fictional company" isn't the blanket pass I thought it was to claim anything. The disclaimer banner covers a lot but it doesn't cover specific false credentials.

Consequences: Brief and site mockups are clean. New tagline fits Fenn's privacy-focused positioning better than "Farmers First" did anyway. Going forward, every named entity, certification, or claim gets triple verified before it goes into any artifact.

---

**Site design updates after the audit.**

Context: Site design was mostly done from earlier in the week but the audit changes (removed claims, new tagline, "Fenn Agritech" instead of "Fenn Agritech Ltd.") needed to be applied to the mockups too.

Decision: Updated copy and removed the deleted claims from the mockups. Didn't do new design work beyond that.

Consequences: Site mockups are now consistent with the cleaned up company brief. Design itself still needs more tweaks.

---

**Wrote the first GRC doc: sub-processor list.**

Context: Needed to start writing actual GRC docs. Sub-processor list felt like the right starting point because it's short, required under UK GDPR Article 28, and public-facing.

Decision: Wrote a full sub-processor list. Vendors: AWS, AWS SES, Stripe, Sentry, Plain.

Rationale: Sub-processors are a foundational doc that every other GRC artifact can reference back to.

Consequences: First real GRC doc shipped. Sets the standard for what the rest need to look like.

---

**Email setup: tried for hours to get a Fenn-branded email, gave up, used personal domain.**

Context: Writing the sub-processor list forced the question of what email to put on the document. Using hello@wichman.io felt weird on a fictional company's GRC artifact, so wanted a Fenn-branded email to keep up the illusion.

Decision: Spent a couple hours trying every workaround:
- Tried signing up for Proton with the fenn subdomain. DNS records already pointing to GitHub Pages for the site, conflicting MX records not allowed.
- Tried Porkbun's email service for a subdomain email. They don't support it.
- Considered SimpleLogin. Same DNS record conflict issue as Proton.
- Tried Cloudflare email routing. Would have meant moving wichman.io's nameservers over to Cloudflare entirely, breaking my existing Proton mail setup. Not willing to migrate my whole email ecosystem just for a fake company email no one's actually going to use.
- Considered hello@fenn.wichman.io directly. That subdomain already had a CNAME pointing to GitHub Pages, can't mix CNAME with MX records on the same host. Would have meant something like hello@mail.fenn.wichman.io. Too long and ugly.
- Considered hosting Fenn at wichman.io/fenn instead. Wouldn't have helped the email issue anyway, and subdomain is the standard convention for portfolio projects with their own deployment.

Eventually gave up on Fenn-branded email entirely. Used personal domain instead: hello@wichman.io for the contact modal (recruiters, general inquiries), privacy@wichman.io for the privacy policy and sub-processor list (data subject rights).

Rationale: After hours of fighting it, gave up on Fenn-branded email entirely. 
Wasn't possible without breaking my existing Proton setup. Defaulted to personal 
domain instead, split into two addresses for some separation: hello@ for general 
contact, privacy@ for the privacy policy (the data subject rights piece is real 
since the site is real, even though the company is fictional).

Consequences: Two clean email surfaces. No Fenn-branded email pretending to be a real company inbox. Hours lost trying to make subdomain email work. Learned a lot about domain configuration constraints and different layers. DNS records conflict in ways that aren't obvious and what I wanted was not possible.

---

## 2026-05-13: Trademark Hell

**Discovered Furrow wouldn't work and switched to Fellow.**

Context: Day after setting everything up as Furrow. Was doing a general "red flag" pass on the whole project to catch obvious issues before going deeper.

Decision: Found out a real UK London-based agritech startup called Furrow already exists (founded 2020, listed on Seedtable as one of the top agritech startups in London). Also discovered John Deere publishes a long-running agricultural magazine called "The Furrow" and Fenn's company brief lists John Deere as an integration partner. Two collisions in the exact same sector. Switched to Fellow.

Rationale: A real UK London-based agritech with the same name is the worst-case version of a name collision. Even for a fictional company, sharing a name with a real competitor in the same city and category looks careless. The John Deere magazine collision was a separate issue but compounded it.

Consequences: Rebuild #1. Had to change the logo, README, repo name, DNS settings in Porkbun, and references throughout the design files. Annoying but not catastrophic. Lost a few hours.

---

**Discovered Fellow wouldn't work either and switched to Fenn.**

Context: Spent more time checking Fellow than Furrow. I used the UK Companies House check.

Decision: Eventually found out about a second website I hadn't been checking: the UK Intellectual Property Office trademark register. Searched "Fellow" there and found two live trademarks. One had a carve-out for caregiver software only (would have been fine) but the second covered Class 42 (software design and development services) with no carve-out aka directly overlapping with B2B SaaS. Back to drawing board. Switched to Fenn.

Rationale: Even if a fictional portfolio company has minimal legal exposure, sharing a name with a registered trademark in your exact sector looks careless or like you didn't do due diligence. The whole point of changing from Furrow was to avoid this.

Consequences: Rebuild #2. Same drill as Furrow - logo, README, repo name, DNS, design file references. Not happy. Fenn cleared both Companies House and the IPO trademark register for the classes that matter (9 and 42) so it would stick.

---

**Learned the UK system the hard way: Companies House and the trademark register are different things.**

Context: Going into this I'm American and didn't know the UK system for company names and trademarks. Assumed checking one source was enough (it was not).

Decision: Spent all of Wednesday figuring out that Companies House and the UK IPO trademark register are two completely separate systems doing two different jobs.

Rationale: Hitting the same kind of issue twice in two days with Furrow then Fellow made it obvious that the name check process I was using wasn't sufficient. Continuing to wing it would have meant a third rebuild, possibly a fourth. Better to stop and actually learn the system than keep guessing.

Consequences: Now understand the two systems are doing different jobs. Companies House is a registry of legal entities with no industry classes while the IPO trademark register protects brand names within specific classes (1-45). For SaaS, Classes 9 (downloadable software) and 42 (cloud/SaaS) are the ones that matter. A name can be free on Companies House and still trademarked in your sector: exactly what happened with Fellow. Going forward both checks have to clear before any setup work.

---

**Discovered there's a small Mac app already called Fenn.**

Context: Doing one final round of due diligence on Fenn before committing for real.

Decision: Found a Mac file-search utility called Fenn (usefenn.com) subscription consumer product. Decided to use the name anyway.

Rationale: The Mac app is owned by a French company. Post-Brexit, EU trademarks no longer automatically cover the UK so they'd 
need a separate UK filing to have any protection here. Plus the fact it's not in agritech and the fact that 
Fenn Agritech is fictional, legal exposure is negligible.

Consequences: Fenn is locked. Slight signaling concern that there's another software product with the same name, but minor. Not worth a third rebuild.

---

## 2026-05-12: Initial Creation

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
