# Hospital-Network-Segmentation
Cisco-based secure network for HIPAA-compliant patient monitoring.
# 🏥 Protecting Patients Through Network Security  
*How I isolated medical devices using Cisco networking fundamentals*

## 📌 The Challenge  
Imagine a busy hospital where patient heart monitors sit on the same network as visitor smartphones. That's not just risky - it's dangerous!  

**My mission**:  
Create a safe digital environment where sensitive medical equipment is protected from general hospital traffic while meeting strict healthcare privacy laws (HIPAA).

**My solution**:  
I built a 3-layer security shield:  
1. **Digital quarantine zones** (VLANs) for medical devices  
2. **Smart traffic filters** (ACLs) blocking non-essential protocols  
3. **Port lockdowns** preventing unauthorized devices from connecting  

## 🔧 Behind the Scenes  
### Our Hospital's Digital Blueprint  
![Network Diagram](Hospital-Network-Segmentation/Hospital_Network_Project/Diagrams
/Complete Hospital Network Architecture Overview.png) 
*Visualizing the secure network design*

### The Brains Behind the Security  
Here's a peek at the digital "rules" I created to protect patient monitors:  
```cisco
! Creating a safe traffic zone for medical devices
ip access-list extended MEDICAL-ONLY  
 permit tcp 192.168.10.0 0.0.0.255 any eq 443  // Allow secure medical data
 deny   tcp any any eq 3389                    // Block risky remote access
