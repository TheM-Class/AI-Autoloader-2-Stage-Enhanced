[README.md](https://github.com/user-attachments/files/28819624/README.md)
# AI-Autoloader-2-Stage-Enhanced
2-Stage AI Intelligent Autoloader with Superior Timings and Special Payload Handling
M///CLASS NEXT-GEN TWO-STAGE PS5 AUTOLOADER Version AI-1



END-USER GUIDE



Firmware 4.03 - 10.01   HD-1080p - 4K-2160p

============================================================



WHAT THIS AUTOLOADER DOES

\-------------------------

This system automates the complete jailbreak and payload-loading process.

It finds your configured ELF/BIN files, loads them in a controlled order,

protects sensitive payloads such as kstuff and etaHEN, displays live PS5

information, and creates a reusable payload set in /data after a clean run.



This project was started to create a stable, fully automatic, easy-to-use,

and informative PS5 autoloader. The goal is less manual payload sending,

fewer timing problems, fewer kernel panics, and clear information about

what the PS5 and autoloader are doing.





QUICK START

\-----------

1\. Create this folder on a USB drive:



&#x20;  ps5\_autoloader



2\. Place your ELF/BIN payloads inside that folder.



3\. Create an autoload.txt file in the same folder.



4\. List one payload filename per line in the order you normally want them:



&#x20;  kstuff\_test2.elf

&#x20;  etaHEN.bin

&#x20;  ftpsrv-ps5.elf

&#x20;  homebrew\_payload.elf



5\. Connect the USB drive and launch YouTube/Y2JB.



The autoloader handles kstuff and etaHEN using its own safety rules, even

when their names appear elsewhere in autoload.txt.





FIRST LAUNCH: PRIMARY AUTOLOAD

\------------------------------

On the first launch, the autoloader:



\- Performs one controlled jailbreak attempt.

\- Starts and verifies the ELF loader on port 9021.

\- Finds autoload.txt on USB or in /data.

\- Loads normal ELF/BIN payloads in sequence.

\- Detects kstuff and etaHEN automatically by filename.

\- Executes the selected special payload dead last.

\- Waits for the final payload to resolve before closing YouTube.

\- Displays loaded, skipped, and failed entries plus total execution time.



**If the entire USB run completes without failures or warnings**, the successful

payload set is copied to:



&#x20;  /data/ps5\_autoloader



**A fresh autoload.txt is created there.** Future primary runs can then operate

without the USB drive. 



**Inteligent built-in automatic data/ps5\_autoloader repair** 





SMART KSTUFF AND ETAHEN RULES

\-----------------------------

\- kstuff and etaHEN require special handling to avoid as many kernel panics

&#x20; as possible.

\- Under normal circumstances, kstuff and etaHEN must not both be sent during

&#x20; the same primary autoload.

\- If both are listed, kstuff receives primary-run priority and **etaHEN** is

&#x20; reserved for the **optional** protected second stage.

\- kstuff can kernel panic YouTube/PS5 when it is sent alongside other

&#x20; payloads, so the autoloader isolates it and sends it dead last.

\- If multiple kstuff files are present, only the largest one is selected.

\- If multiple etaHEN files are present, only the largest one is selected.

\- The selected kstuff payload always runs dead last.

\- Older, duplicate, or lower-priority candidates are safely skipped.

\- The selected etaHEN is prepared for the protected second stage.

* The Jailbreak itself can still Kernal Panic your console 
* wait **10** seconds **after** the controller message clears to run Y2JB.



Filename detection is case-insensitive. The name only needs to contain

"kstuff" or "etaHEN" and end in .elf or .bin.





SECOND LAUNCH: ARM ETAHEN

\-------------------------

When the PS5 is already jailbroken, the exploit and primary autoloader are

skipped. The prepared etaHEN payload is not sent immediately. The autoloader

first arms the protected etaHEN stage and asks the user to close and relaunch

YouTube.



The bright red/green pulsing warning reports:



&#x20;  Secondary etaHEN rerun armed.

&#x20;  Close and relaunch YouTube to confirm execution.



This extra launch is intentional. It keeps etaHEN optional and separated from the primary

autoload and requires a clean relaunch before execution.





THIRD LAUNCH AND LATER SAFETY

\-----------------------------

Repeated etaHEN loading can make the environment unstable. This build uses

a restart-to-confirm safety cycle.



Third launch:



\- The relaunch is accepted as confirmation.

\- etaHEN execution #1 is sent through the active ELF loader.

\- The execution state is secured before the payload is sent.



Fourth launch:



\- etaHEN is not sent.

\- The final recovery resend is armed.

\- The close-and-relaunch warning appears again.



Fifth launch:



\- The final relaunch is accepted.

\- etaHEN execution #2 is sent.



Every later launch is permanently blocked from sending etaHEN again.

The two-execution allowance is reset only when a fresh successful primary

autoload prepares a new etaHEN cache.



WHY ETAHEN CAN RUN TWICE

\------------------------

The two-execution maximum is a recovery feature for a failed etaHEN Toolbox

load. If etaHEN itself loaded but Toolbox did not open correctly, the user

can perform one protected etaHEN resend without rebooting the PS5.



The second execution is not intended for routine repeated loading. After

etaHEN has been executed twice, the autoloader permanently locks additional

etaHEN sends until a fresh primary autoload resets the allowance.



Maximum protected sequence:



\- Second launch: arm and skip.

\- Third launch: etaHEN execution #1.

\- Fourth launch: arm and skip.

\- Fifth launch: etaHEN execution #2.

\- Sixth and later launches: permanently locked.





LIVE INFORMATION PANEL

\----------------------

The banner provides live information including:



\- PS5 firmware

\- Detected Title ID

\- Network address

\- Jailbreak status

\- Current and last payload type

\- ELF loader status on port 9021

\- FTP status on ports 1337, 2120, 2121, and 2122

\- Klog status on port 3232



On an already-jailbroken launch, the banner becomes an information panel

and continues refreshing available service information.





SCREEN MESSAGE GUIDE

\--------------------

\[STAGE]  A task is currently running.

\[OK]     The task completed successfully.

\[SKIP]   The item was intentionally or safely skipped.

\[ERROR]  A required operation failed and needs attention.

\[DATA]   Informational details, payload names, or summary information.



A skipped duplicate or lower-priority special payload is normal. Review the

reason shown beside the entry before treating a SKIP message as a problem.





IMPORTANT SAFETY NOTES

\----------------------

\- Do not close YouTube while payloads are still loading.

\- Wait for the final success summary or the relaunch instruction.

\- Do not resend etaHEN manually while the protected second stage is active.

\- Do not rename unrelated payloads with "kstuff" or "etaHEN" in the name.

\- Keep only payloads intended for your PS5 firmware and configuration.

\- Do not alter internal timing values unless you are developing and testing.

\- A failed USB run will not replace the existing working /data payload set.

\- If the jailbreak fails, reboot the PS5 and try again.





AUTOLOAD.TXT NOTES

\------------------

\- Use one filename per line.

\- Blank lines are ignored.

\- Lines beginning with # are comments.

\- Lines beginning with @ display a notification.

\- JavaScript files ending in .js can also be executed.

\- Use exact filenames, including the .elf, .bin, or .js extension.



TIMINGS ARE FULLY AUTOMATIC

\---------------------------

Users do not need to adjust, calculate, or troubleshoot payload timings in

autoload.txt.



Any timing or delay instructions in autoload.txt are permanently ignored.

The autoloader uses its own protected internal polling system instead:



\- It checks whether the ELF loader is ready.

\- It waits while the loader is busy.

\- It sends the next payload only when the loader is available.

\- It confirms payload completion and applies the required resolve grace.



This readiness-based design replaces unreliable fixed delays. Payload speed,

file size, screen resolution, and normal service startup differences do not

require users to rewrite timing values. The process is fully automatic.



Example:



&#x20;  # Normal payloads

&#x20;  ftpsrv-ps5.elf

&#x20;  homebrew\_payload.elf



&#x20;  # Automatically managed special payloads

&#x20;  kstuff\_latest.elf

&#x20;  etaHEN\_latest.bin





BUILD IDENTITY

\--------------

Y2JB by **Gezine**

Autoloader by M///Class | AI Build



2 Stage Autoloader With Execution Armed Safety



