## hand-hi-gene
Using technology to prevent Healthcare Associated Infections (HAI)

# Problem definition
* Healthcare associated infections (HAI) represent a significant source of morbidity and mortality; there are over 1.4M HAI/year worldwide. 
* In the United States, one out of every 25 hospitalized patients is afflicted by a HAI (Magill SS, Edwards JR, Bamberg W, et al. Multistate Point-Prevalence Survey of Health Care–Associated Infections. New England Journal of Medicine 2014; 370:1198-208.) In other developed countries the rate can be as high as 1 in 20.
* Every year in the US, there are approximately 80,000 deaths per year from HAI, which are estimated to cost the healthcare system over $33B annually.
    * Specifically in 2002, there were 30,665 for bloodstream infections, 13,088 for urinary tract infections, 8,205 for surgical site infections, and 11,062 for infections of other sites.
* HAI data is collected by CMS (https://www.medicare.gov/hospitalcompare/data/healthcare-associated-infections.html) and reported publicly. 
    * There are several types of HAIs tracked by Medicare, including Catheter Associated Urinary Tract Infections (CAUTI), Central Line Associated Blood Stream Infections (CLABSI), Surgical Site Infections (SSI). There are also specific organisms responsible for infections that are tracked: Methicillin Resistant Staphylococcus Aureus (MRSA), 
    * Since 2014, Medicare has reduced reimbursement for hospitals with the highest rates of HAI; specifically the bottom 25% of hospitals have their reimbursement reduced by 1%.
* Despite this progress, over 10% of hospitalized patients experience a HAC of which HAI is the most common.
* A simple, low-tech approach his highly effective for preventing infection
    * Since 1846, when Ignaz Semmelweis demonstrated the effectiveness of hand washing to prevent nosocomial and iatrogenic infections, Hand hygiene is the single most effective method of preventing HAI.
    * Unfortunately, compliance with hand hygiene is practiced less than half the time.
    * Even with modern innovations - such as alcohol based gel hand washes - [hand hygeine compliance has improved from 38% to 55%]. (https://www.ncbi.nlm.nih.gov/pubmed/11996615)
    
* Thus simply improving hand washing compliance would prevent the majority of HAIs and resulting in tens of thousands of lives and billions of dollars saved annually.
    * For example, [an intensive hand hygiene improvement campaign demonstrated a sustained 10% improvement in hand hygiene compliance](https://wwwnc.cdc.gov/eid/article/22/9/15-1440_article) (as ascertained by observers) and a 14% reduction in the rate of HAI-CDIs over a 2 year period.
* Unfortunately, prior approaches have failed for multiple reasons including:
    * imperfect data collection: inability to collect both gel and hand washing data, high failure rate in registering events
    * lack of user feedback
    * poor incentive structure: punishment instead of reward system
    * ineffective business case
    
# Proposed Solution

* Using an innovative combination of off-the-shelf IOT technologies it is possible to build a system of behavioral nudges to enhance hand washing compliance.
    * A BLE beacon signals when a user has entered an area that requires hand hygeine
    * The user washes hands using foaming sanitizer or soap and water; a wearable on the wrist or finger detects the hand washing event and registers it
    * Users who forget to gel in or out receive a gentle nudge in the form of a vibrations or other innocuous alert
    * Data is collected and users can receive rewards for achieving hand hygiene compliance; data can also be used for hospital wide initiatives and incentives
* Users who maintain a high rate of hand hygiene are given short term rewards (‘achievement unlocked’) within the app and longer term bonuses (performance bonus partially tied to % hand hygiene compliance)

## Technology
* BLE beacon signifies entry into a room that requires hand hygiene (signal strength, accuracy, etc)
    * [Whitepaper on BLE beacon technology](http://pages.silabs.com/rs/634-SLU-379/images/Whitepaper-Developing-Beacons-with-Bluetooth-Low-Energy-Technology.pdf)
* Hand hygiene events are detected using NFC on gel dispensers or on sinks
* Data is uploaded to the cloud via WiFI
* What hardware is required?
    * Wearable (Apple Watch, Fitbit, Amazfit, Mi Band, etc). Must have NFC and the ability to run outside code. 
* ESP32 - can do BLE beacon, WiFi. Would need another board for NFC. 
* Soap dispenser


# Technology challenges
* Range of BLE beacons can range from 1 meter to 500 meters depending on transmit power. Probably the transmit power of the beacons placed in rooms would need to be low. There could be significant error in accurately detecting room entry. 
* NFC must be very reliable. If the dispenser fails to trigger it would compromise trust in the system. 
* Ideally the unit cost should be very low


# Alternative approaches/competitors
* current approaches to measure hand hygiene are inaccurate, cumbersome, and frequently are confounded by the Hawthorne Effect. These approaches are also extremely expensive. Approaches used to measure hand hygiene compliance include:
    * Paid observers
    * Video cameras
* companies who are doing something similar using alternative technologies
    * [Clean Hands Safe Hands](https://cleanhands-safehands.com/) - *Mesh network of XigBee equipped sensors* attached to soap dispensers
    * [Biovigil](https://www.biovigil.com/) - *Infrared (IR) sensors* on badges detects proximity to soap dispensers
    * [HyGreen](https://www.infectioncontroltoday.com/hand-hygiene/hygreen-system-ensures-healthcare-workers-wash-their-hands) - *smell sensors* detect the presence of alcohols to confirm that hands have been washed
    
# Early Stage Proof of Concept Work can be broken into stages
1. NFC equipped soap dispenser - a user activates the device using an RFID tag
2. Soap dispenser that can upload data to the cloud - an [ESP8266](https://en.wikipedia.org/wiki/ESP8266) that can detect soap dispenser activation an upload a data packet
3. Bluetooth beacon that can detect proximity between a user and a soap dispenser
4. Wearable able to communicate over NFC
5. A virtual machine server that can accept messages and display basic statistics about use

    
    
