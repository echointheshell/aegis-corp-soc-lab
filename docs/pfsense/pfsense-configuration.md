# pfSense Configuration Guide

## Initial Web Access & Setup Wizard

### Accessing pfSense Web Interface
1. Open web browser and navigate to: **https://192.168.10.1**
2. Accept the SSL certificate warning (self-signed certificate)
3. **Default Login Credentials:**
   - **Username:** `admin`
   - **Password:** `pfsense`

### Setup Wizard Configuration


We are greeted with a the Setup Wizard, which allows us to configure basic settings in pfsense in order to get up to speed.
Not all settings here are relevant to the configuration of the firewall, so we will only go over areas that are changed below.


![Wizard Start](/assets/pfsense-wizard-start.png)


#### Step 1: General Information
- **Hostname:** `lan-fw-01`
- **Domain:** `aegiscorp.org`
- **Primary DNS Server:** `Empty`
- **Secondary DNS Server:** `Empty`
- **Override DNS:**
  - [x] Checked (allows pfSense to use your hosts DNS settings)


![Domain Information](/assets/pfsense-wiz-2.png)


#### Step 2: Time Server Information
- **Time Server Hostname:** `2.pfsense.pool.ntp.org`
- **Timezone:** Select your timezone here


![NTP](/assets/pfsense-wiz-3.png)


#### Step 3: Configure WAN Interface
- **General Configuration:**
  - Since we have already configured WAN during setup, we do not need to change any options here besides those stated
- **Reserved Networks:**
  - [ ] Block RFC1918 Private Networks (uncheck for lab environment since our simulated WAN address is a private address)
  - [x] Block bogon networks (uncheck for lab environment)
 

![WAN Config](/assets/pfsense-wiz-4.png)


#### Step 4: Configure LAN Interface
- **LAN IP Address:** `192.168.10.1`
- **Subnet Mask:** `24` (255.255.255.0)


![LAN Config](/assets/pfsense-wiz-5.png)


#### Step 5: Set Admin Password
- **Admin Password:** `[Choose strong password]`
- **Confirm Password:** `[Confirm password]`


![Password](/assets/pfsense-wiz-6.png)


#### Step 6: Reload Configuration
- Click **Reload** to apply all settings
- Wait for pfSense to reload configuration


![Confirm Reload](/assets/pfsense-wizard-reload.png)
![Reload Done](/assets/pfsense-wizard-done.png)
![Dashboard](/assets/pfsense-dash.png)


#### Step 7: Test Internet Connectivity
- Navigate to **Diagnostics > Ping**
- Enter `www.google.com` and execute to ping Google
- This should resolve the hostname to test DNS as well as verify WAN is set up correctly


![Check net connection](/assets/pfsense-ping-test.png)


---

## DHCP Services Configuration

### DHCP Configuration

Coming Soon!

---

## DNS Services Configuration

### DNS Resolver Settings

Coming Soon!

---

## Firewall Rules Configuration

Coming Soon!

---

## NAT Configuration

Coming Soon!

