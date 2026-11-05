# Research

Written 2026-11-05 during Task 03, because no Task 02 research file was in the repo. Sources were read through web search summaries, not as full papers, so check the original before quoting a number. No learners have been interviewed: the problem statements in `brief.md` come from personal experience and observation.

## Is the problem real?

Yes, unfinished self-paced learning is well documented, though these figures cover free online courses, not self-learners in general.

- About 4% of registrants finished, in a University of Pennsylvania study of about 1 million registrants across 16 Coursera courses. ([Higher Ed Dive](https://www.highereddive.com/news/mooc-completion-rate-just-4-study-says/202425/))
- Completion ranged from 0.7% to 52.1%, with a median of 12.6% of enrolled students, across 221 courses in Jordan's 2015 study. It varied with course length. ([Lancaster University](https://www.research.lancs.ac.uk/portal/en/publications/massive-open-online-course-completion-rates-revisited-assessment-length-and-attrition(d34cbd4a-a392-41d9-84b7-3520c3cd866f).html))

**Caution:** many people sign up with no plan to finish, so these numbers overstate how many people failed at something they really wanted. Our audience is people who really want the skill, and we found no figures for that group.

## Does a person finding out actually work?

**The evidence is mixed. This is the biggest risk to the idea, because the whole app rests on this consequence.**

- **Against:** in a field experiment with 364 online weight-management clients, the group with a reputational commitment reported *lower* weight loss over 12 weeks. The authors suggest commitment "overload". ([UCL, Savani 2018](https://discovery-pp.ucl.ac.uk/10056803/9/Savani_Commitment%20Devices%20for%20Health%20%28Savani%202018%29.pdf))
- **Weak:** in an experiment with 134 college students who shared a study goal with a partner, the partner's status produced only a non-significant trend in committed study time. ([Journal of Emerging Investigators](https://emerginginvestigators.org/articles/21-213))
- **Partly for:** an analysis of a commitment-contract platform found that success depended on how financial and social commitments were combined. It is observational, not a controlled trial, and the mix includes money, which we don't use. ([KAIST](https://koasas.kaist.ac.kr/handle/10203/288658))
- **Not found:** any large randomized trial of a friend acting as an accountability partner. Popular claims such as "doubles your odds" came from blogs that cite no study, so we are not using them.

**What this means for us:** none of these studies tested our exact setup, a person the learner chose who is emailed after 48 quiet hours. Whether it works is what the first version tests, so the app can't promise it works. It also supports making sure emails feel like a warning rather than a punishment.

## What already exists

| Tool | How it creates a consequence | Why it isn't this project |
|---|---|---|
| [Beeminder](https://habi.app/insights/accountability-apps/) | Automatic money penalty when you go off track; graphs your trend toward a target | The consequence is money, and our learners may have none to stake |
| [stickK](https://focusbear.io/blog-post/focus-bear-vs-stickk-make-your-life-easier-with-goal-setting-2) | Commitment contracts with money at stake; reviews mention a referee | Closest to our idea. We couldn't confirm what its referee does, so check this before claiming we are different |
| [Focusmate](https://www.focusmate.com/blog/beeminder-focusmate-integration) | Live silent work sessions on camera with a stranger | Helps during a session, but says nothing about a deadline or the next step |
| To-do lists, timers, phone blockers | None | Ignored or switched off (`brief.md`) |

**Possible gap:** a known person finding out, with no money involved, tied to a course deadline and a visible risk level. This comes from a quick search, mostly of blogs and vendor pages, so it isn't proof that nothing like it exists.

## Technical checks for `stack.md`

- **Render free tier:** reported to sleep after 15 minutes idle, so the first visit is slow. ([Render community](https://community.render.com/t/why-is-my-service-shutting-down-after-only-a-couple-of-minutes-and-all-data-is-lost/17760))
- **Supabase free tier:** reported to pause after about 7 days with no activity, and long-paused projects can be deleted. The hourly check should keep it active. ([SimpleBackups](https://simplebackups.com/blog/supabase-free-tier-paused))
- **Brevo free tier:** 300 emails a day. ([Brevo help](https://help.brevo.com/hc/en-us/articles/208580669))
- **Brevo with a Gmail sender is an unsolved risk.** We can't add authentication records to gmail.com, so warnings may fail authentication or land in spam. We found no source that settles this, so it has to be tested with a real send. ([Unspam](https://unspam.email/deliverability/brevo))

## Still to do

- Talk to at least three self-learners, and ask whether they would really name a person.
- Find out what stickK's referee does.
- Test a real Brevo send to Gmail and Outlook inboxes.
