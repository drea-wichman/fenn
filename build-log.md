## 2026-06-10: Published Business Continuity Plan

**Wrote and published Business Continuity Plan v1.0.**

Context: Next doc in the queue after retention.

Decision: Wrote FENN-POL-006. It covers what counts as critical, how fast each part needs to come back, how Fenn recovers, who runs the response, and how it's tested. Kept everything in the UK even in a disaster, and added a second backup copy held in the UK with a different provider.

Rationale: AWS only has one UK location, so the usual disaster plan of switching to another region would move customer data out of the country. Kept it in the UK instead, and accepted that recovery from a total London outage takes longer (up to three days), since it's an extremely rare event. Also made an outage during a busy farming window like spraying or harvest count as more serious than one in the quiet season, because it is.

Consequences: Sixth policy live.

---

## 2026-06-08: Published Data Retention Policy

**Wrote and published Data Retention Policy v1.0.**

Context: Next policy in the queue. Started it on a flight, finished it after.

Decision: Wrote FENN-POL-005. Retention periods by data category, a 60-day export window before deletion, automatic deletion confirmations to every customer, a legal holds section, and deletion events logged as evidence.

Rationale: Went 60 days on the export window instead of 30 because a farmer who hypothetically cancels mid-season needs real time to pull their data out. Client-side encryption means holding the ciphertext an extra month isn't a privacy risk, so customer friendly won. Added legal holds so automated deletion can't wipe data that's under dispute.

Consequences: Fifth policy live. Ready for next doc.

---

## 2026-05-30: Two More Policies and Some Cleanup

**Wrote Incident Response Plan v1.0.**

Context: My next priority after access control and information security policies.

Decision: Six response phases, three severity tiers (P1/P2/P3), separate notification section with controller vs. processor split. Tied the encryption exemption back to Fenn's customer-managed-key architecture.

Rationale: Controller vs. processor was the biggest gap in the first draft. Didn't know the difference going in.

Consequences: Third policy shipped.

---

**Wrote Vendor Risk Management Policy v1.0.**

Context: Sub-processor list existed but nothing explained how vendors get on it or how they're managed.

Decision: Three vendor risk tiers (Critical/Standard/Low), contract requirements, cross-border transfer assessment, cloud services and software supply chain sections.

Rationale: Had to separate Critical (operational risk to Fenn) from sub-processor (processes customer personal data). JumpCloud is one but not the other.

Consequences: Fourth policy shipped.

---

**Fixed sub-processor list contact email.**

Decision: Changed privacy@wichman.io to privacy@fenn.io. No legal requirement for a real working contact email on this document.

Consequences: Fiction stays clean. Real contacts stay on the real website.

---

**Added Jack Lowe to Behind Fenn page.**

Decision: Added Jack below founders, simpler layout, no quote. Security consultancy background. Not financial services since Cian covers that and not government since that wouldn't be the best fit for this privacy-first company.

Consequences: Three named people on the site plus the other employees.

---

## 2026-05-19: Finish Design, Security Check, and Start New Doc

**Set up site security + ran first performance audit.**

Context: Wanted both sites clean and secure before adding more pages.

Decision: Researched best ways to check site security. Found and enabled GitHub's built-in security options on both repos. Ran npm audit on Fenn. Ran PageSpeed on both.

Rationale: Static sites don't have as many ways to get attacked but I'm using open source packages so there's always a risk. Wanted something watching automatically versus me doing them manually.

Consequences: Dependabot watches Fenn and Secret Protection blocks credential commits on both. Resized Fenn hero from 4.2MB to 898KB to improve score. Apparently Lighthouse fails on a fade-in animation for wichman.io, ignoring. Made checklist for core git terminal commands/workflow.

---

**Migrated trust center to Astro Content Collections.**

Context: The sub-processor list was built by copying its text directly into the website code. Adding the Access Control Policy the same way would mean keeping two copies of every future policy in sync.

Decision: Set up Content Collections in the site repo. Now every policy lives as a single markdown file and the site builds the page from it. The sub-processor list stayed as it was since it's a different kind of doc.

Rationale: One time setup cost paid back from second policy onward.

Consequences: New streamlined workflow for adding policies. Single source of truth for the readable docs stays in Fenn repo.

---

**Wrote and published Access Control Policy v1.0.**

Context: First formal policy doc. Sub-processor list was already done but it's a disclosure, not a policy.

Decision: Wrote FENN-POL-001. Covers identity management (JumpCloud), authentication (hardware keys mandatory for all employees, no SMS or software MFA), least privilege, privileged access (small standing PAWG plus JIT for everyone else), JML, quarterly access reviews, remote access. Maps to 13 ISO 27001:2022 controls and UK GDPR Art. 32.

Rationale: Access Control was the right starting point because it's foundational and maps cleanly to ISO 27001. Picked hardware keys for everyone because Fenn's privacy-focused positioning needs phishing-resistant MFA. Picked the standing PAWG plus JIT model instead of pretending Fenn runs on zero standing privilege. A company with 100 employees needs a few people with always-on admin access. Tacking on language about working toward zero standing privilege felt like theater.

Consequences: First formal policy shipped. Sets the YAML and section structure for future policies.

---

**Live site is up to date.**

Context: Contact modal still didn't feel right after yesterday. Spent time on the layout.

Decision: Stacked the three contact links vertically instead of a horizontal row. Kept modal width and font sizes fixed so proportions read closer to square. Pushed all local changes.

Rationale: Horizontal row read too wide. Live was far behind local.

Consequences: Modal locked. Live site is caught up to local.

---

## 2026-05-18: Design Change Day

**Locked design, tokens, and structure.**

Context: The site has existed structurally but today I sorted out the cosmetics.

Decision:
- **Welcome modal**: acknowledgment required. No X, localStorage gated, "I understand" required to enter. Body text now names Fenn as a fictional GRC portfolio project.
- **How It Works**: changed to vertical stack with three columns and integrations under each step.
- **Design tokens locked**: New color palette confirmed. Buttons and modal designs confirmed.

Rationale: The welcome modal is the disclaimer for every visitor so it being dismissible is not what we want. The localStorage flag prevents the modal from reappearing on every page. Three column How It Works shows the auto capture pitch at a glance versus old vertical layout.

Consequences: Tokens documented. Smaller polish (padding, font sizes, saturation, section colors) not itemized here.

---

## 2026-05-17: GRC doc format standards

**Locked the format for policies vs. case studies vs. public disclosure docs.**

Context: Started planning the internal policies for the Trust Center. Realized I didn't have a consistent format and was about to wing it across essentially all docs.

Decision: Three patterns by doc type:
- **Policies**: YAML front matter with `title`, `document_id`, `version`, `effective_date`, `last_reviewed`, `next_review`, `owner`, `approver`, `scope`, `framework_mapping`.
- **Case studies**: existing header pattern (NHS WannaCry and AGCO already use it). No YAML.
- **Public disclosure docs**: varies. Verify against real-world examples before assuming YAML applies.

Rationale: YAML front matter is the auditor recognizable convention for internal policy docs. Makes version, ownership, and framework mapping scannable. Case studies and public docs don't need it because their audiences don't care.

Consequences: When the next six policies get written the format is already known.

---

## 2026-05-16: Site Build Push

**Built every page that wasn't the landing page.**

Context: After the week of design and a working landing page, the rest of the site was placeholder. /trust-center, /trust-center/sub-processor-list, /behind-fenn, /privacy, /terms, /building-fenn, and /404 all needed to be built.

Decision: Built all of them in one push. Cream legal pages, dark green editorial pages, consistent design tokens throughout.

Consequences: Site is structurally complete. The six internal policies and the DPA still say "In development" on the Trust Center page. Templates are wired up so when I write the content the pages exist to drop it into.

---

**Renamed /policies to /trust-center.**

Context: While building the page, realized "Policies" wasn't standard B2B SaaS terminology for what this page is.

Decision: Renamed the page, file, URL, footer link, header link, and landing page button. Section label on the landing page still reads "Policies" as a descriptor, but the destination is named correctly.

Rationale: Trust Center is the actual industry convention.

---

**Decided the sub-processor list lives as a polished page on Fenn, not a GitHub link.**

Context: The sub-processor list already exists as markdown in the fenn repo. Question was whether to surface it on the site as a real styled page or link out to GitHub from the Trust Center.

Decision: Built a styled page at /trust-center/sub-processor-list. GitHub link to the source markdown is in the page metadata.

Rationale: Customer-facing legal documents need to look like real company documents. A real Series B SaaS wouldn't link out to a raw markdown file from their Trust Center.

---

**Decided the build log stays on GitHub.**

Context: Same question as the sub-processor list but for the build log.

Decision: Build log stays as a GitHub link from /building-fenn, not a styled page on the site.

Rationale: Different audience expectations. Legal documents belong on the polished site. Engineering decision logs belong on GitHub. Also, porting to Astro would be real work for small benefit.

---

**Verified legal compliance against ICO sources, not template generators.**

Context: Before locking in the privacy policy and terms, wanted to confirm what was actually required for this specific site versus what template generators include because every site has it.

Decision: Researched ICO guidance, UK GDPR Article 13 requirements, PECR cookie rules, and the 2026 DUA Act updates. Confirmed for this site: privacy notice required (any site processing personal data including IPs needs one), terms not required (only required for sites selling goods or services), cookie banner not required (no cookies set), separate cookies page not required (one line in the privacy policy is enough).

Rationale: Copy and pasting from generic templates leads to sections that don't apply (Children's, separate Cookies, AI/automated decision-making) making the document longer and harder to read without adding value.

Consequences: Privacy policy covers Article 13 items 1-9 and skips item 10 because it doesn't apply. Terms page kept despite not being legally required because it's where copyright over original portfolio work is asserted.

---

**Banner CTA now points to /building-fenn instead of being dead.**

Context: The banner at the top of every page had a dead "Learn more" button that opened a modal that didn't exist.

Decision: Replaced the button with an anchor link to /building-fenn.

Consequences: Visitors can actually read the project context now.

---

**Added two photos to the landing page.**

Context: Landing page was text heavy and felt like a PowerPoint slide.

Decision: Added two full width agricultural photos acting as section breaks rather than illustrations inside sections.

Rationale: Two photos at symmetric points gives the eye somewhere to rest twice. Both photos are from Unsplash, no attribution required. Aerial image is rotated in CSS and dimmed because its saturation was jarring with current palette.

Consequences: Landing page reads as a designed product page now instead of a deck. Learned how to adjust photos in VS.

---

**Pushed everything to GitHub.**

Context: Long session, lots of changes.

Decision: Staged all changes, committed, pushed to main.

Consequences: GitHub Pages will pick it up within a few minutes. Got noticeably more comfortable in VS Code and Terminal this session: Cmd+F for in-file search, Ctrl+G to jump to a specific line, running grep and sed in one Terminal window while npm run dev keeps the site running in the other, navigating between line numbers instead of scrolling. Nice.

---

## 2026-05-15: Starting the Build Log

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
