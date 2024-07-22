If you are following me , you are know that I usually post to recommend you awesome free/payed learning resources. I tend to stay away from what I call "politics" that are happening here on LinkedIn more than on social media.

Now, I would like to comment a bit on the CrowdStrike incident. In the end, I would leave you with a professional analysis from someone who knows a lot about Windows internals(task manager, windows activation just to name a few of his achievements).

I would like to start by pointing out the obvious. All those posts making fun of Windows administrators on a Friday, while *Nix administrators are chillin, are biased. Linux itself has the thing called kernel panic, and because it's on black screen, rather than blue, it can blend in. Here are a few issues that *Nix administrators had to deal with, caused by CrowdStrike:

- https://www.reddit.com/r/debian/comments/1c8db7l/linuximage61020_killed_all_my_debian_vms
- https://access.redhat.com/solutions/7068083

Now, for your information what is a Windows bluescreen? Simply put, it's an uncaught exception in the kernel or an error condition that the kernel doesn't know how to handle. In order to protect the system and not to do damage, the kernel shuts itself down. That is reasonable. At least you as an user get the chance to recover/restore the system, this is better than to reimagine it from the beginning.

Second thing that you need to know, is that privileged applications, such as antimalware solutions, need low level access , to see inside the OS, thus the need to access ring 0, the kernel space. In order to do so, these applications install a driver, thus extending the Windows kernel space.
In the case of this incident, the problem (as leaked by a X post, https://x.com/taviso/status/1814762302337654829/photo/1), points to a null pointer dereference in a CrowdStrike driver. Immediately you can tell, that this is not a security incident, but rather a QA/release management issue. I have worked a bit as a developer, and I had to pass several filters before pushing the code to production, like code reviews, testing pipelines(that included SAST and DAST as well), running the code on a testing platform and so on. This is more an organizational area that I do not wish to go to. I have seen some conspiracy theoreticians that said it surely must have been premeditated.

Third, there is a group of people that are recommending to go to Rust development. Rust is gaining a lot of popularity in the Windows and *Nix kernel space and it's memory safe. The direction of the development is steered by the most experienced devs in the organization, and ultimately they will balance out the pros and cons of each language and choose what they see as the obvious choice for their project. This is a situation when a group is trying to get unfair technical advantage, by saying things like "surely with Rust this wouldn't happen".

Forth, the other competitors of CrowdStrike, are trying to get business advantage, by promoting their solutions as being technical safe from stuff like this. This is again political, and I am sure in a similar fashion, CrowdStrike has done the same in the past, for companies doing their marketing like this, you won't get any respect from me.

Fifth, and this is a personal take on the recovery process from this incident. The recovery process is manual, and a bit involved, this is why some of the affected systems are not fully up. Microsoft is providing a tool, that is speeding up the recovery process, and you can find it here:

- https://techcommunity.microsoft.com/t5/intune-customer-success/new-recovery-tool-to-help-with-crowdstrike-issue-impacting/ba-p/4196959

Simply put, in a crisis like this you need the man power, people to run the tool and restore the systems. What I would wish as a feature for the Windows operating system is something like a list of previous kernels or a filesystem snapshot, when critical stuff like drivers are pushed into the OS. I know that there is the last know good configuration, but that is more about the apps, and things stored in windows registry. Other things like a full system backup, would have taken longer to restore, but with the same successful outcome.

In the end, as promised I would like to recommend you to watch Dave Plummer's technical analysis of the situation:

- https://www.youtube.com/watch?v=wAzEJxOo1ts

Cheers and be sympathetic!

