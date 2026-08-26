# Building Fenn

Fenn is my first GRC portfolio project, a fictional UK agritech SaaS built from scratch. The brief, the website, and the documents exist as if the company were real. New to tech as a whole but drawn to GRC in theory, I chose to go beyond writing isolated case studies because there's a limit on what's publicly available about how real companies do this work, and a limit on my understanding of it as a result. I "hired" myself to do the work without the pressure of real risk, deadlines, or consequences.

Building Fenn as a privacy-focused company was my first instinct and priority. Next I had to choose the features that would actually create that privacy: customer-held keys, no surveillance default, Proton internally, the sub-processor list. The third step was communicating that privacy to Fenn's customers. "Your land. Your data. Your decision." captured Fenn's commitment in a straightforward but marketable phrase.

## The blueprint

- **Agritech.** SaaS and GRC are unfamiliar enough on their own without piling a third unknown industry on top.
- **UK-based.** Building Fenn under UK GDPR, the Data Protection Act 2018, and ICO guidance allows me to become familiar with the regulatory environment I'll be navigating for school and placement.
- **B2B SaaS at Series B.** This is the stage where GRC genuinely starts to matter. The company is big enough to have real legal obligations (data processor duties, sub-processor disclosures, DPAs) and small enough that one person can model the full scope end to end.

## Lessons learned

- **Verify, then version.** Every citation in this set was checked against legislation.gov.uk or ICO guidance. Months later, a law changed, and what looked like an error in an older document was just the world moving after the document was written. Compliance documents are snapshots. Staying aware of what changes and when matters, but the move is the same one any company would make: version forward, don't rewrite history. Each version is evidence of what was in place and when.
- **Built to agree.** What felt like redundancy across the deliverables turned out to be traceability. Each one examines the same decision from a different angle, and when they all agree, that's the evidence that the system holds together. That consistency is how I make sure Fenn stays compliant and the company I set out to build.
- **Small details aren't.** I spent weeks planning Fenn's privacy model and architecture before writing a single document. Even so, I got the document taxonomy wrong, and months later a fact check caught a vendor listed in the wrong country. Both seemingly small errors, yet both required retrofitting every document that referenced them. A quick naming decision on document one becomes structural by document ten, and a single discrepancy in one deliverable ripples across the entire project and website.

## My method

Every document, every decision, every claim, was workshopped line by line and verified against primary sources including legislation.gov.uk and ICO guidance. For the full decision trail, see the [build log](https://github.com/drea-wichman/fenn/blob/main/build-log.md).
