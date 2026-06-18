# MLB-Hits-Model-
A fully automated Python model that figures out which MLB hitters are actually "hot" based on how hard they've been hitting the ball — plus a tracker that logs how every pick turns out so I can see if it really holds up over a full season.

The goal is telling apart guys who are actually hot from guys who just look hot. Batting average is way too noisy over a short stretch — it's fluky and rewards lucky bloop hits — but how hard you hit the ball is much more stable. So I built the whole thing around recent exit velocity (EV) instead of recent results.
A hitter only makes the board if he clears every parameter I set — a mix of recent exit-velocity and hard-contact signals, the opposing-pitcher matchup, and the game's projected run environment. I'm keeping the exact thresholds to myself since that's the part that makes it work, but the point is nobody lands on the board on a hunch. They're there because they passed every check.
The ones who qualify get ranked on two boards — Hot Hitters, and a tighter Hot Hitters 95+ cut for balls hit 95+ mph (Statcast's hard-hit line).

Fully automated
The whole thing runs on its own every day, no manual work:
Pulls fresh Statcast data from Baseball Savant each morning
Rebuilds both boards and re-checks every hitter against the qualifying parameters
Factors in that day's pitching matchups and projected game environment
Once games go final, logs the results and updates the running record automatically

Built with
Python · Google Apps Script · Google Sheets · Statcast / Baseball Savant
<img width="1920" height="872" alt="Screenshot 2026-06-08 123457" src="https://github.com/user-attachments/assets/effe303e-460f-4998-a650-9467d01cf897" />


