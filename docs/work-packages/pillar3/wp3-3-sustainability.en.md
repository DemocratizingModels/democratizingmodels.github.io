# WP 3.3: Organization and Sustainability

## Overview

For data standards, longevity and overall success are closely tied to community engagement. To ensure commitment and buy-in from relevant stakeholders, this work package is specifically focused on establishing the long-term sustainability of the DEMOS standard and its associated community beyond the funding period.

**Lead:** TUDO

## Core Principle

The DEMOS standard must remain viable, maintained, and responsive to community needs long after the initial 3-year funding period concludes. This requires establishing transparent governance structures, clear contribution pathways, and active community participation mechanisms.

## Governance Structure

### Steering Committee

**Formation:** 2027.Q3

**Purpose:**
- Oversee review of proposed changes to the standard
- Ensure both technical and community feedback are integrated
- Coordinate long-term development priorities
- Maintain consistency with DEMOS principles
- Resolve disputes and conflicts

**Responsibilities:**
- Review and approve proposed standard changes
- Coordinate with stakeholder representatives
- Define and maintain release schedule
- Oversee CI/CD maintenance
- Ensure documentation remains current
- Manage community communication channels

**Composition:**
- Technical experts from diverse domains
- Representatives from major software implementations (C++, Python, Julia engines)
- Community advocates ensuring accessibility
- Regular rotation through election process

### Election and Renewal Process

**Establishment:** 2028.Q3

To ensure fresh perspectives and continued community engagement:

**Process:**
1. **Nomination period:** Open call for steering committee candidates
2. **Candidate statements:** Public descriptions of vision and qualifications
3. **Community input:** Stakeholder representatives provide feedback
4. **Election:** Community vote or selection by stakeholder representatives
5. **Term limits:** Regular rotation to prevent stagnation

**Frequency:** Regular renewal cycle (e.g., annual or biannual rotation of subset of members)

## Stakeholder Representation

### Nomination Process

**Timeline:** 2028.Q1

**Identification of Stakeholders:**

Representatives will be nominated from:

**Experimental Collaborations:**
- ATLAS, CMS (TUDO, LMU, TUM)
- LHCb, COMPASS (RUB-H)
- Belle II (MPP, LMU)
- BES III (JGU)
- IceCube, Auger (TUM, RUB-A)
- GERDA, MAJORANA, LEGEND (MPP)
- HIBEF, NIF collaborations (HZDR)

**Software Frameworks:**
- ROOT/RooFit developers
- PyHF maintainers
- BAT.jl developers
- CRPropa collaboration
- AmpTools developers
- Domain-specific analysis frameworks

**Theoretical Communities:**
- Lattice QCD practitioners
- Chiral EFT nuclear theorists
- Amplitude theory community
- Warm dense matter theorists
- Strong-field QED community

**Data Repositories:**
- HEPData team
- Zenodo team
- RODARE and other domain repositories

**Formal Procedure:**
- Each stakeholder group nominates representative(s)
- Representatives commit to active participation
- Regular communication with their communities
- Term-limited positions with renewal option

### Responsibilities

Stakeholder representatives will:
- Communicate DEMOS developments to their communities
- Gather feedback and feature requests
- Participate in standard review processes
- Advocate for domain-specific needs
- Facilitate adoption within their groups
- Contribute to prioritization decisions

## Review and Contribution Process

### Standardized Review Process

**Establishment:** 2027.Q4

**Purpose:** Ensure all proposed changes undergo consistent evaluation

**Process Stages:**

1. **Proposal Submission**
   - Via GitHub/GitLab pull/merge request
   - Must include: motivation, specification, examples, tests
   - Proposer may be community member or consortium member

2. **Automated Validation**
   - CI/CD pipeline checks (2028.Q1)
   - Syntax validation
   - Backward compatibility testing
   - Documentation completeness check

3. **Technical Review**
   - Steering committee evaluates technical merit
   - Domain experts assess domain-specific implications
   - Engine maintainers evaluate implementation feasibility

4. **Community Feedback Period**
   - Proposal publicized to mailing list and communication channels
   - Open comment period (e.g., 2-4 weeks)
   - Stakeholder representatives gather input

5. **Revision and Refinement**
   - Proposer addresses feedback
   - Iterative improvement

6. **Approval Decision**
   - Steering committee makes final determination
   - Considers technical merit, community need, implementation cost
   - Clear documentation of decision rationale

7. **Implementation and Integration**
   - Approved changes merged
   - Engines updated to support new features
   - Documentation updated
   - Included in next release

### Contribution Guidelines

Clear guidelines will be established covering:
- Code style and conventions
- Documentation requirements
- Testing expectations
- Backward compatibility policies
- Deprecation procedures
- Attribution and authorship

## Release Management

### Release Schedule

**Definition:** 2028.Q2

**Purpose:** Regular, predictable integration of approved changes

**Proposed Cadence:**
- **Major releases:** Annually (new features, structural changes)
- **Minor releases:** Quarterly (bug fixes, small enhancements)
- **Patch releases:** As needed (critical fixes)

**Release Process:**
1. Feature freeze period before major releases
2. Beta testing phase with community
3. Release candidate review
4. Formal release with changelog and migration guide
5. Announcement via all communication channels

**Versioning:**
- Semantic versioning (MAJOR.MINOR.PATCH)
- Clear documentation of breaking vs. non-breaking changes
- Deprecation warnings before removal of features

## Communication Infrastructure

### Asynchronous Communication Platform

**Establishment:** 2027.Q3

**Platform:** Mattermost or similar

**Purpose:**
- Enable community members to ask questions
- Share feedback and experiences
- Collaborate on challenges
- Announce updates and events
- Foster community connections

**Channels:**
- General discussion
- Domain-specific channels (hadron, nuclear, neutrino, astro, laser, particle)
- Technical support
- Development coordination
- Announcements

### Mailing List

**Establishment:** 2027.Q3

**Purpose:**
- Official announcements (releases, events, major decisions)
- Distribution of user feedback surveys
- Periodic newsletters

**Management:**
- Archive of past communications
- Subscription management
- Clear policies for appropriate use

### User Feedback Surveys

**Schedule:** 2027.Q3 onwards (regular intervals, e.g., semi-annually)

**Distribution:** Via mailing lists and portal

**Content:**
- User satisfaction metrics
- Feature requests and priorities
- Pain points and challenges
- Adoption barriers
- Success stories
- Demographic information (optional, for inclusivity assessment)

**Analysis:**
- Steering committee reviews results
- Informs development priorities
- Identifies underrepresented groups
- Measures progress toward goals

## Technical Sustainability

### CI-Based Maintenance

**Implementation:** 2028.Q1

**Continuous Integration Pipelines:**
- Automated testing of all engines
- Cross-language compatibility checks
- Documentation build and link checking
- Example model validation
- Performance regression testing
- Security vulnerability scanning

**Continuous Deployment:**
- Automatic updates to portal and documentation
- Engine package releases (PyPI, Julia registry, etc.)
- Docker container updates for MaaS

**Monitoring:**
- Service health checks
- Usage analytics (respecting privacy)
- Error tracking and alerting
- Performance metrics

### Long-Term Hosting

**Strategies:**
- Leverage institutional commitments (RUB, HZDR, CERN connections)
- Utilize sustainable research infrastructure (e.g., through ErUM-Data ecosystem)
- Mirror critical repositories across multiple locations
- Plan for data archival and preservation

### Software Dependencies

**Management:**
- Minimize external dependencies where possible
- Pin versions for reproducibility
- Monitor for deprecated dependencies
- Plan migration paths for aging technologies
- Document all dependencies clearly

## Inclusivity and Representation

### Targeted Outreach

**Efforts include:**
- Actively recruit underrepresented groups for steering committee
- Provide multiple participation pathways (synchronous/asynchronous)
- Offer mentorship for new contributors
- Ensure events are accessible (virtual options, financial support, accessibility accommodations)
- Translate key documentation into multiple languages (if resources permit)

### Barriers to Participation

**Identification and Mitigation:**
- Survey community about participation barriers
- Provide documentation for various skill levels
- Create "good first issue" pathways for new contributors
- Recognize and value diverse contributions (not just code)
- Establish code of conduct and enforcement mechanisms

## Risk Mitigation

### Personnel Shortages

**Challenge:** Key personnel leave or reduce involvement

**Mitigation:**
- Document all processes thoroughly
- Cross-train multiple people on critical tasks
- Distribute responsibilities across consortium
- Build community capacity for self-governance
- TUDO allocates significant personpower as safety buffer

### Delay in Release Schedule

**Challenge:** Approved changes not integrated on schedule

**Mitigation:**
- TUDO significant personpower allocation for integration tasks
- Clear prioritization process
- Realistic scheduling with buffer time
- Community contributions for lower-priority items
- Automated tools reduce manual burden

### Declining Community Engagement

**Challenge:** Community participation decreases over time

**Mitigation:**
- Regular surveys identify declining interest early
- Refresh outreach efforts based on feedback
- Showcase successful use cases
- Organize periodic community events
- Ensure standard remains relevant to current research

### Competing Standards

**Challenge:** Alternative standards emerge and fragment community

**Mitigation:**
- Emphasize interoperability from the start
- Engage early with potential competing efforts
- Focus on clear value proposition
- Build strong community loyalty through good governance
- Remain flexible and responsive to needs

## Success Indicators

By 2028.Q3 and beyond:

**Governance:**
- ✓ Steering committee formed with representatives from diverse domains
- ✓ Election process documented and tested
- ✓ Stakeholder representatives nominated from major collaborations

**Processes:**
- ✓ Standardized review process operational
- ✓ At least 5 community-contributed changes successfully integrated
- ✓ Release schedule defined and followed

**Communication:**
- ✓ Active communication channels with regular participation
- ✓ Mailing list with 100+ subscribers
- ✓ First user feedback survey completed with actionable insights

**Technical:**
- ✓ CI/CD pipelines operational and maintaining code quality
- ✓ All engines covered with 70%+ test coverage
- ✓ Documentation automatically built and deployed

**Community:**
- ✓ Models contributed by groups outside original consortium
- ✓ Community members elected to steering committee
- ✓ Positive user satisfaction scores

## Connection to Other Work Packages

WP 3.3 integrates with:

- **WP 1.1 (Harmonizing):** Mechanism for adding new primitives
- **WP 1.2 (Engines):** CI/CD for engine testing and releases
- **WP 2.1 (Front-end):** Portal hosts communication and documentation
- **WP 2.2 (Back-end):** CI/CD for model validation and registry updates
- **WP 3.1 (Documentation):** Governance and contribution processes documented
- **WP 3.2 (Showcasing):** Community contributions expand model gallery

## Long-Term Vision (Beyond 2028)

The sustainability mechanisms established in WP 3.3 aim to create a self-sustaining ecosystem where:

- The steering committee continues to evolve with community needs
- Regular releases integrate community contributions
- New domains adopt the standard organically
- Educational institutions incorporate DEMOS into curricula
- The standard adapts to technological changes (new languages, platforms)
- DEMOS becomes the de facto standard for model sharing in ErUM

**10-Year Horizon:**
- DEMOS standard is routinely used across all major ErUM collaborations
- Models are published alongside papers as standard practice
- Next generation of researchers learns DEMOS as fundamental skill
- Cross-disciplinary collaborations enabled by shared model language
- Educational resources at all levels utilize DEMOS models
- Industry applications leverage open scientific models

## Deliverables Timeline

| Milestone | Timeline | Status |
|-----------|----------|--------|
| Asynchronous communication platform | 2027.Q3 | Mattermost or similar |
| Steering committee formation | 2027.Q3 | Initial members |
| User feedback surveys begin | 2027.Q3 | Semi-annual |
| Standardized review process | 2027.Q4 | Documented and operational |
| Stakeholder representatives nominated | 2028.Q1 | From all major groups |
| CI-based maintenance pipelines | 2028.Q1 | Full automation |
| Release schedule defined | 2028.Q2 | Major/minor/patch cycle |
| Election process established | 2028.Q3 | Ready for first election |
| Self-governance operational | 2028.Q3 | Community-driven |

## Personnel

**Lead:** TUDO (0.5 FTE)

**Support:** All consortium members for:
- Stakeholder representative nomination
- Steering committee participation
- Review process engagement
- Communication channel activity

Through comprehensive organization and sustainability planning, WP 3.3 ensures the DEMOS standard transcends the initial funding period to become a lasting contribution to the ErUM research ecosystem.
