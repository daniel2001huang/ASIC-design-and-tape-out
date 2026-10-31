# Lab 8 individual report  (copy as reports/<your_name>.md - one per member)
Name: LiKuan Huang
NetID: daniel2001huang
Team: team1

## 1. What I personally did in this lab
(2-5 sentences. Be specific: which steps you drove, what you typed/read.)
I loaded the course environment using `source /mnt/nfs-scratch/ecen-689-nowka/kit/env.sh`. I imported the CPU source files with `ghdl -i` and ran `ghdl -m --std=08 core` to build the core. I created `microwatt_top.vhdl` from the provided skeleton. Finally, I used the script to synthesis the design, and get a area.

## 2. Problems I encountered
(Every error message you personally hit. Paste the exact line.)
After submitting the synthesis jobs, I ran squeue -u $USER to check their status. Both jobs remained pending (PD), and the queue displayed the following lines:
717934  adademic lab8_syn daniel20 PD       0:00      1 (QOSMaxCpuPerUserLimit)
718869  adademic lab8_syn daniel20 PD       0:00      1 (Priority)

When I checked again, job 718869 also showed (QOSMaxCpuPerUserLimit). I could not obtain the synthesis results through these pending jobs at that time.

## 3. How each problem was resolved
(What fixed it, how you figured it out, or who/what helped.)
I checked the job status using squeue -u $USER and observed that the synthesis jobs had not started. I then used the login-node fallback script provided in the lab manual by running bash lab8/synth_core_loginnode.sh, and monitored its output with tail -f synth_core_tmux.log. This run produced a chip-area result, which I recorded in A4.