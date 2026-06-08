# MLB-Hits-Model-
MLB Hits Model
A Python model that predicts which MLB hitters are about to produce, based on how hard they've been hitting the ball — paired with a tracker that records how every prediction turns out, so I can see whether it actually holds up over a full season.
The idea
How hard you hit the ball is way more stable than batting average over a short stretch. So when a hitter's contact is great but his results haven't caught up, the production is usually coming — and the model is a systematic way to find those guys before the box score does.
For each hitter it builds a daily projection from three inputs: recent exit velocity (the main driver), the opposing pitcher and handedness matchup, and the game's projected run environment. It then ranks hitters on two boards — Hot Hitters, and a tighter Hot Hitters 95+ cut for balls hit 95+ mph (Statcast's hard-hit line).
Two targets, two signals
The model predicts two things that measure different skills:

1+ hit — pure individual. Getting a hit is almost entirely on the batter, so it's the cleanest test of the exit-velocity signal.
2+ hits + runs + RBIs — individual plus team. Runs and RBIs need teammates, so a hitter can crush the ball and still miss this one if the lineup goes quiet.

Because of that, only the 2+ H+R+RBI target gets a filter requiring a projected team run total above 3.5 — matching the filter to the part of the stat that's outside the hitter's control. The 1-hit target skips it, since a hit doesn't care how many runs the team scores.
Tracking how it performs
The tracker locks in each prediction before games, records the real result after they go final, and keeps a running win-loss record across the season — so I can't fool myself by cherry-picking a hot stretch.
548-300 

Record for playes with over .5 hits in a game 
Built with
Python (scraping) · Google Apps Script (daily automation) · Google Sheets · Statcast / Baseball Savant 
Next: move the pipeline off Google Sheets into a real database, add expected stats like xwOBA, and test how well-calibrated the predicted probabilities are.
