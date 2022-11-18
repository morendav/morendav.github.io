
# Iran Protests

Source: The intercept (Archive: https://archive.ph/gYSEG)

> Iran’s tight grip on the country’s connection to the global internet has proven an effective tool for suppressing unrest.


### SIAM
> Part of Iran’s data clampdown may be explained through the use of a system called “SIAM,” a web program for remotely manipulating cellular connections made available to the Iranian Communications Regulatory Authority. The existence of SIAM and details of how the system works, reported here for the first time, are laid out in a series of internal documents from an Iranian cellular carrier that were obtained by The Intercept.
>  SIAM is a computer system that works behind the scenes of Iranian cellular networks, providing its operators a broad menu of remote commands to alter, disrupt, and monitor how customers use their phones.
> The tools can slow their data connections to a crawl, break the encryption of phone calls, track the movements of individuals or large groups, and produce detailed metadata summaries of who spoke to whom, when, and where.
> Referred to within SIAM as “Force2GNumber,” the command allows a cellular carrier to kick a given phone off substantially faster, more secure 3G and 4G networks and onto an obsolete and extremely vulnerable 2G connection. Such a network downgrade would simultaneously render a modern smartphone largely useless and open its calls and texts to interception — both of obvious utility to a government clamping down on public gatherings and speech.
  > While not directly mentioned in the manuals, downgrading users to a 2G connection could also expose perilously sensitive two-factor authentication codes delivered to users through SMS. The Iranian government has previously attempted to undermine two-factor authentication, including through malware campaigns targeting dissidents.

Additional info (source: https://www.goincognito.co/info-irans-surveillance-and-spy-tools-leaked/)
* The system they are using is called SIAM. You can read the leaked user guide for SIAM by going HERE
* SIAM is embedded directly in the local phone company, so in this case, spyware does not need to be installed on the target phone. (However, in theory, they could plant spyware directly into the operating system via a SIAM compromised SIM card)
* SIAM gives the Iranian authorities many surveillance capabilities, including but not limited to:
a. Disconnecting individuals as well as broad swaths of the population from the web
b. Slowing data connections to a crawl
c. Break the encryption of phone calls (read my tip about blocking 2g connections HERE)
D. Track the movements of individuals or large groups,
E. Produce detailed metadata summaries of who spoke to whom, when, and where.


## Tracking phones
* imei over sim
  > SIAM’s tracking of unique device identifiers means that swapping SIM cards, a common privacy-preserving tactic, may be ineffective in Iran since IMEI numbers persist even with a new SIM, explained a network security researcher who reviewed the manuals and spoke on the condition of anonymity, citing their safety.
