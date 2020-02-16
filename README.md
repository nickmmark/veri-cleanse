# Veri-Cleanse
Using IoT technology to monitor hand hygeine compliance and prevent Healthcare Associated Infections (HAI)

## Problem definition
* [Healthcare associated infections](https://www.cdc.gov/hai/data/index.html) (HAI) represent a significant source of morbidity and mortality:
   * Worldwide, [the WHO estimates that there are ***_hundred of millions_*** of HAI per year](https://www.who.int/gpsc/country_work/gpsc_ccisc_fact_sheet_en.pdf). Newborns in low to middle income countries are particularly susceptible to HAI, and it is estimated [that **4-56% of neonatal deaths are due to HAI**](https://www.who.int/gpsc/country_work/gpsc_ccisc_fact_sheet_en.pdf), particularly in Southeast Asia.
   * In the United States, there are over ***1.4 million HAI/year*** and approximately [one out of every 25 hospitalized patients is afflicted by a HAI](https://www.nejm.org/doi/10.1056/NEJMoa1306801?url_ver=Z39.88-2003&rfr_id=ori:rid:crossref.org&rfr_dat=cr_pub%3dwww.ncbi.nlm.nih.gov). In other developed countries the rate can be as high as 1 in 20.
* Every year in the US, [there are approximately 80,000-90,000 deaths per year from HAI, which are estimated to cost the healthcare system over $33B annually](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2827870/). 
* There are several different types of HAI. They can classified by _site of infection_ (e.g. bloodstream or urinary infection), _route of infection_ (e.g. catheter related, ventilator associated , surgical site infections), or _specific causative organisms_ (e.g. methacillin resistant staphylococcus aures; MRSA). In 2002 in the US, there were: 
   * 30,665 bloodstream infections, 
   * 13,088 for urinary tract infections, 
   * 8,205 for surgical site infections, and 
   * 11,062 for infections of other sites.
* [HAI data is collected by CMS](https://www.medicare.gov/hospitalcompare/data/healthcare-associated-infections.html) and reported publicly. Medicare tracks several different HAIs, including Catheter Associated Urinary Tract Infections ([CAUTI](https://www.cdc.gov/hai/ca_uti/uti.html)), Central Line Associated Blood Stream Infections ([CLABSI](https://www.cdc.gov/hai/bsi/bsi.html)), Surgical Site Infections ([SSI](https://www.cdc.gov/hai/ssi/ssi.html)). There are also specific organisms responsible for infections that are tracked: Methicillin Resistant Staphylococcus Aureus ([MRSA](https://www.cdc.gov/hai/organisms/mrsa-infection.html)), Vancomycin Resistant Enteroccocus ([VRE](https://www.cdc.gov/hai/settings/lab/vreclinical-laboratory.html)), Clostridium Difficile Infection ([CDI](https://www.cdc.gov/hai/eip/cdiff-tracking.html)).
    * Since 2014, ***_Medicare has reduced reimbursement for hospitals with the highest rates of HAI_***; specifically the bottom 25% of hospitals have their reimbursement reduced by 1%. In 2019, [CMS announced that 800 US hospitals would have thier Medicare reimbursement reduced](https://www.medicare.gov/hospitalcompare/HAC-reduction-program.html).
    * Due to technological advances (chlorhexidine replacing iodine disinfectant, alcohol gel supplanting soap and water, etc) and changes in reimbursement such as the [Medicare Hospital Acquired Condition Reduction Program (HACRP)](https://www.cms.gov/Medicare/Medicare-Fee-for-Service-Payment/AcuteInpatientPPS/HAC-Reduction-Program), hospitals have dedicated substantial effort to preventing HAIs.

* A simple, low-tech approach his highly effective for preventing infection
    * Since 1846, when [Ignaz Semmelweis](https://en.wikipedia.org/wiki/Ignaz_Semmelweis) demonstrated the effectiveness of hand washing to prevent nosocomial and iatrogenic infections, *Hand hygiene has proven to be the single most effective method of preventing HAI.*
    * Unfortunately, **proper hand hygiene is practiced less than half the time**.
    * Even with modern innovations - such as alcohol based gel hand washes, [which have improved hand hygeine compliance from 38% to 55%](https://www.ncbi.nlm.nih.gov/pubmed/11996615), ***proper hand hygeine is neglected almost half the time.***
    * There is a [marked gender gap with women substantially more likely to practice proper hand hygeine](https://slate.com/technology/2020/02/women-hand-washing-more-than-men-why-coronavirus.html).
    
* Thus **improving hand washing compliance would prevent the majority of HAIs and resulting in tens of thousands of lives and billions of dollars saved annually**.
    * For example, [an intensive hand hygiene improvement campaign demonstrated a sustained 10% improvement in hand hygiene compliance](https://wwwnc.cdc.gov/eid/article/22/9/15-1440_article) (as ascertained by observers) and a 14% reduction in the rate of HAI-CDIs over a 2 year period.
![effectiveness of prior intervention](https://github.com/nickmmark/hand-hi-gene/blob/master/figures/example_intervention.jpg)
    
* Unfortunately, prior approaches have failed for multiple reasons:
    * imperfect data collection: high failure rate in capturing events, inability to collect both gel and hand washing data, 
    * lack of feedback to users: inability to capture individual level data and provide meaningful feedback
    * concerns about patient privacy: cameras and observers are potential breaches of privacy
    * poor incentive structure: punishment instead of reward system
    * ineffective business case: despite the potential ROI, high cost hardware may not be feasible to implement

    
## Our Proposed Solution
* The objective of this project is to build a low cost hardware/software solution that encourages and documents hand hygeine
* Using an innovative combination of off-the-shelf IOT technologies it is possible to build a system of behavioral nudges to enhance hand washing compliance.
    * A BLE beacon signals when a user has entered an area that requires hand hygeine
    * The user washes hands using foaming sanitizer or soap and water; a wearable on the wrist or finger detects the hand washing event and registers it
    * Users who forget to gel in or out receive a gentle nudge in the form of a vibrations or other innocuous alert
    * Data is collected and users can receive rewards for achieving hand hygiene compliance; data can also be used for hospital wide initiatives and incentives
* Users who maintain a high rate of hand hygiene are given short term rewards (‘achievement unlocked’) within the app and longer term bonuses (performance bonus partially tied to % hand hygiene compliance)

![proposed end to end solution](https://github.com/nickmmark/hand-hi-gene/blob/master/figures/proposed_sysem_overview.png)

* This system could be valuable both in the developed and developing world. Sadly, more than 150 years after Semmelweis demonstrated the benefit of handwashing in obstetrics, HAI remains one of the leading causes of infant mortality in the developing world. Thus A low cost easy ot use system of monitoring hand washing could millions worldwide.

* Although the largest benefit might be realized in the healthcare space, there are many groups that could benefit from this product
   * hospitals
   * clinics
   * skilled nursing facilities (SNFs)
   * restaurants
   * parents - trying to encourage hand hygeine at home


## Technology
* BLE beacon signifies entry into a room that requires hand hygiene (signal strength, accuracy, etc)
    * [Whitepaper on BLE beacon technology](http://pages.silabs.com/rs/634-SLU-379/images/Whitepaper-Developing-Beacons-with-Bluetooth-Low-Energy-Technology.pdf)
* Hand hygiene events are detected using NFC on gel dispensers or on sinks
* Data is uploaded to the cloud via WiFI 
* What hardware is required?
    * Wearable (Apple Watch, Fitbit, Amazfit, Mi Band, etc). Must have NFC and the ability to run outside code. 
    ![example of a wearable](https://media1.popsugar-assets.com/files/thumbor/ABbf1Km7ItJgV7noHCre5k8QDfE/fit-in/1024x1024/filters:format_auto-!!-:strip_icc-!!-/2019/04/30/974/n/1922729/bbaaabb15cc8cac5330f21.46671604_fitbit/i/Fitbit-Inspire.png | width=100)
* [ESP32](https://www.espressif.com/en/products/hardware/esp32/overview) - powerful microcontroller that can can do BLE, BLE beacon, WiFi. Well suited to many IoT applications.
* [ESP8266](https://en.wikipedia.org/wiki/ESP8266) - WiFi enabled, lower cost and optimized for sending data packets to the cloud.
* [RC552](http://www.hobbytronics.co.uk/mfrc522-reader) - a low cost NFC/RFID module compatible with 13.56mhz communication standard
* Soap dispenser - simple low cost unit for prototyping
    ![example of a soap dispenser](https://images-na.ssl-images-amazon.com/images/I/814v0LYlM2L._AC_SY679_.jpg | width=100)

## Technology challenges
* Range of BLE beacons varies from 1 meter to 500 meters depending on transmit power. 
    * Probably the transmit power of the beacons placed in rooms would need to be low. 
    * There could be significant error in accurately detecting room entry. 
    * Unclear if the beacons should be on the people (like on badges or in a wearable) or the dispensers. Both could work.
* NFC must be very reliable. If the dispenser fails to trigger it would compromise trust in the system. For this reason it might make more sense to make the dispensers activate using the conventional IR sensors and only detect the user with NFC.
* Ideally the unit cost should be very low (<$25) to encourage widespread adoption, particularly in the developing world.
* The units should be very parsimonious with sending data over hospital WiFi; monopolizing bandwidth would be a big problem for hospitals.

## Advantages of this approach
* Low unit cost ([ESP32/ESP8266 cost $4-12](https://makeradvisor.com/esp32-vs-esp8266/), RFID tags cost <$0.50/each, and [entry level wearables can be purchased for $27-50](https://www.techradar.com/news/best-cheap-activity-trackers))
* Proven technologies (RFID, NFC, BLE, WiFi) are used to build the stack ensuring reliability/scalability
* Carrots not stick (motivate users with rewards not penalties)

## Alternative approaches/competitors
* current approaches to measure hand hygiene are inaccurate, cumbersome, and frequently are confounded by the [Hawthorne Effect](https://en.wikipedia.org/wiki/Hawthorne_effect). These approaches are also extremely expensive. Approaches used to measure hand hygiene compliance include:
    * Paid observers
    * Video cameras
* companies who are doing something similar using alternative technologies
    * [Clean Hands Safe Hands](https://cleanhands-safehands.com/) - *Mesh network of XigBee equipped sensors* attached to soap dispensers
    * [Biovigil](https://www.biovigil.com/) - *Infrared (IR) sensors* on badges detects proximity to soap dispensers
    * [HyGreen](https://www.infectioncontroltoday.com/hand-hygiene/hygreen-system-ensures-healthcare-workers-wash-their-hands) - *smell sensors* detect the presence of alcohols to confirm that hands have been washed
    
## Early Stage Proof of Concepts
The initial work can be broken into discreet stages; each of these POCs includes seperate documentation
1. NFC equipped soap dispenser - a user activates the device using an [RFID tag](https://en.wikipedia.org/wiki/Radio-frequency_identification)
2. Soap dispenser that can upload data to the cloud - an [ESP8266](https://en.wikipedia.org/wiki/ESP8266) that can detect soap dispenser activation an upload a data packet
3. Bluetooth beacon that can detect proximity between a user and a soap dispenser
4. Remote control/activation of a soap dispenser
5. Wearable able to communicate with the soap dispenser
6. A server (platoform agnostic) that can accept messages from multiple soap dispensers
7. A simple dashboard for interpreting the usage data

## Goal Deliverable
A low cost unit for detecting hand hygeine and uploading the data to the cloud. The results should be surfaced in a manner that is easy to interpret.

## Product Name(s)
* Working name: ***_Veri-cleanse_*** - (pronounced ˈver-​ə ˈklenz) portmanteau of "verify" and "cleanse"
* Alternatives:
  * ***_Sani-check_*** - (pronounced sa-nə chek) portmanteau of "sanitize" and "check"

## License
- [ ] TBD what license best covers this work


## Abbreviations
- HAI - healthcare associated infections
- CAUTI - catheter associated urinary tract infection
- CLABSI - central line associated blood stream infection
- MRSA - methicillin resistant staphylococcus aureus
- CDI - clostridium difficile infection
- IOT - internet of things
- NFC - near field communication
- BLE - Bluetooth low energy beacons
- RFID - radiofrequency identification

## Versioning/Known issues/To-Do
- 

## References/See also
* Magill SS, Edwards JR, Bamberg W, et al. [Multistate Point-Prevalence Survey of Health Care–Associated Infections](https://www.nejm.org/doi/10.1056/NEJMoa1306801?url_ver=Z39.88-2003&rfr_id=ori:rid:crossref.org&rfr_dat=cr_pub%3dwww.ncbi.nlm.nih.gov). _New England Journal of Medicine_ 2014; 370:1198-208.
* Stone PW, [Economic burden of healthcare-associated infections: an American perspective](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2827870/), _Expert Rev Pharmacoecon Outcomes Res. Author manuscript_ 2010
