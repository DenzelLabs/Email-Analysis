# Email-Analysis

<br><br>

## Objective

<p>To investigate a phishing email by analyzing its metadata, headers, malicious URLs, and associated malware samples in order to trace the origin, identify persistence mechanisms, and understand the threat landscape.</p>

<br><br>

## Skills Learned
<ul>
  <li>Email header analysis (SPF, DKIM, return path)</li>
  <li>IP tracing and threat intelligence lookup</li>
  <li>Malware detection and classification (Coinminer, BitRAT, AsyncRAT)</li>
  <li>Hash analysis using VirusTotal and URLhaus</li>
  <li>Registry and persistence mechanism investigation</li>
</ul>

<br><br>

## Tools USed
<ul>
  <li>Notepad++ (email inspection)</li>
  <li>URLhaus (malware distribution check)</li>
  <li>Malpedia (malware family identification)</li>
  <li>VirusTotal (hash and URL scanning)</li>
  <li>VMRay (registry persistence analysis)</li>
</ul>


<br><br>


## Questions

<p>Q1: Identifying the sender's IP address with specific SPF and DKIM values helps trace the source of the phishing email. What is the sender's IP address that has an SPF value of softfail and a DKIM value of fail?</p>
<strong>Answer: 18.208.22.104</strong><p>used Notepad++ to open the Email</p>
<br>
<img width="566" height="71" alt="image" src="https://github.com/user-attachments/assets/42089ba5-bb72-47b8-b58c-714c5d71d974" />

<br><br>

<p>Q2: Understanding the return path of an email is essential for tracing its origin. What is the return path specified in this email?</p>
<strong>Answer: erikajohana.lopez@uptc.edu.co</strong>
<br>
<img width="395" height="47" alt="image" src="https://github.com/user-attachments/assets/dd66a8df-a35d-44e7-ac54-99ca4e879dc2" />

<br><br>

<p>Q3: Identifying the source of malware is critical for effective threat mitigation and response. What is the IP address of the server hosting the malicious file related to malware distribution?</p>
<strong>Answer: 107.175.247.199</strong>
<br>
<img width="798" height="105" alt="image" src="https://github.com/user-attachments/assets/e9d97f92-c44c-42b1-8846-fe4762feaa8f" />


<br><br>

<p>Q4: Identifying malware that exploits system resources for cryptocurrency mining is critical for prioritizing threat mitigation efforts. The malicious URL can deliver several malware types. Which malware family is responsible for cryptocurrency mining?</p>
<strong>Answer: Coinminer</strong>
<br>
<p>Pasted http://107.175.247.199/loader/install.exe into Urlhaus to check if it’s a known malware distributor.</p>
<img width="1276" height="309" alt="image" src="https://github.com/user-attachments/assets/bbd6a578-fa02-4cf3-b0fc-84d04a8951d7" />
<br>
<p>On Malpedia, saw that Coinminer malware hijacks system resources to secretly mine cryptocurrency.</p>
<img width="1161" height="221" alt="image" src="https://github.com/user-attachments/assets/0667fe43-81b6-48d8-84f6-cc2ccce51a16" />

<br><br>

<p>Q5: Identifying the specific URLs malware requests is key to disrupting its communication channels and reducing its impact. Based on the previous analysis of the cryptocurrency malware sample, what does this malware request the URL?</p>
<strong>Answer: http://ripley.studio/loader/uploads/Qanjttrbv.jpeg</strong>
<p>Click the link for more info, then copy the SHA-256 (Coinminer)</p>
<img width="1276" height="309" alt="image" src="https://github.com/user-attachments/assets/bbd6a578-fa02-4cf3-b0fc-84d04a8951d7" />
<img width="1267" height="283" alt="image" src="https://github.com/user-attachments/assets/9e11fc5a-3d97-4de3-b344-094c469f4837" />

<p>Paste the SHA-256 hash from URLhaus into VirusTotal to retrieve the malware URL</p>
<img width="1371" height="501" alt="image" src="https://github.com/user-attachments/assets/39aaa283-d5f9-4acd-91f5-ba9c0a30c1af" />
<br><br>

<p>Q6: Understanding the registry entries added to the auto-run key by malware is crucial for identifying its persistence mechanisms. Based on the BitRAT malware sample analysis, what is the executable's name in the first value added to the registry auto-run key?</p>
<strong>Answer: Jzwvix.exe </strong>
<p>Copy the SHA-256 hash from URLhaus (BitRAT) and pasted it on VirusTotal</p>
<img width="1283" height="282" alt="image" src="https://github.com/user-attachments/assets/18bf0f69-ad1c-4470-bc34-e9b49e978396" />
<img width="1360" height="210" alt="image" src="https://github.com/user-attachments/assets/757d163e-b1de-4f64-bfda-619e84901b72" />
<p>On the Community tab, check the analysis report</p>
<img width="702" height="292" alt="image" src="https://github.com/user-attachments/assets/3745be5f-cfe3-4bb2-91a9-e68fc56d8ce9" />
<p>On the VMRay website, navigate to Registry Run Keys / Startup Folder, then click Persistence.</p>
<img width="842" height="215" alt="image" src="https://github.com/user-attachments/assets/b4343cf5-8f5d-40be-a1dd-a3f13105dbc1" />



<br><br>

<p>Q7: Identifying the SHA-256 hash of files downloaded from a malicious URL is essential for tracking and analyzing malware activity. Based on the BitRAT analysis, what is the SHA-256 hash of the file previously downloaded and added to the autorun keys?</p>
<strong>Answer: bf7628695c2df7a3020034a065397592a1f8850e59f9a448b555bc1c8c639539</strong>
<p>Locate the SHA-256 value under Sample Information</p>
<img width="1091" height="337" alt="image" src="https://github.com/user-attachments/assets/fe1e711d-0db5-4f64-9c8b-d7ac7f8d77b4" />

<br><br>

<p>Q8: Analyzing the HTTP requests made by malware helps in identifying its communication patterns. What is the URL in the HTTP request used by the loader to retrieve the BitRAT malware?</p>
<strong>Answer: http://107.175.247.199/loader/server.exe</strong>
<p>On VirusTotal, go to the Relations tab to find the URL in the HTTP request used by the loader to retrieve BitRAT</p>
<img width="1367" height="492" alt="image" src="https://github.com/user-attachments/assets/6e229b44-8e00-41bc-a310-f65b9cde7790" />

<br><br>

<p>Q9: Introducing a delay in malware execution can help evade detection mechanisms. What is the delay (in seconds) caused by the PowerShell command according to the BitRAT analysis?</p>
<strong>Answer: 50</strong>
<p>In VirusTotal’s Behavior tab, check the Process Tree section for any PowerShell commands. Look for a Base64-encoded PowerShell command.</p>
<img width="969" height="254" alt="image" src="https://github.com/user-attachments/assets/dde5b29c-795f-4e8a-9632-528adf3f82b2" />
<p>Go to CyberChef website. Paste → Decode from Base64 → Remove null bytes.</p>
<img width="1532" height="616" alt="image" src="https://github.com/user-attachments/assets/50b77589-9b6f-4f7b-9eb4-32c8259ff55c" />

<br><br>

<p>Q10: Tracking the command and control (C2) domains used by malware is essential for detecting and blocking malicious activities. What is the C2 domain used by the BitRAT malware?</p>
<strong>Answer: 
gh9st.mywire.org</strong>
<p>On the Community Tab, check the Hatching Triage</p>
<img width="868" height="223" alt="image" src="https://github.com/user-attachments/assets/6c1eecd9-6af1-49fd-890e-44089a18373d" />
<p>Within the Triage Website, go to the Malware Config section to locate the C2.</p>
<img width="597" height="432" alt="image" src="https://github.com/user-attachments/assets/95736310-f983-46e3-a082-56fcfdce9aeb" />

<br><br>

<p>Q11: Understanding how malware exfiltrates data is essential for detecting and preventing data breaches. According to the AsyncRAT analysis, what is the Telegram Bot ID used by this malware?</p>
<strong>Answer: bot5610920260</strong>
<p>Copy the SHA-256 from URLhaus (AsyncRAT). Then paste it on VirusTotal</p>
<img width="1280" height="283" alt="image" src="https://github.com/user-attachments/assets/d9296c89-9367-4694-845d-300126f3881d" />

<p>On the Community Tab, check the Hatching Triage</p>
<img width="829" height="208" alt="image" src="https://github.com/user-attachments/assets/f76e0d93-b907-4f1c-af1d-84e074893c49" />

<p>Navigate to Dridex, click api.telegram.org, and find the Bot ID</p>
<img width="1179" height="351" alt="image" src="https://github.com/user-attachments/assets/6e52d5d2-7a61-44f2-8862-622ed963acf7" />











