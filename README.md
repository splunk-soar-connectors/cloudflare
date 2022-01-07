[comment]: # "Auto-generated SOAR connector documentation"
# Cloudflare

Publisher: Splunk Community  
Connector Version: 1\.0\.1  
Product Vendor: Cloudflare  
Product Name: Cloudflare  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.9\.39220  

This app integrates with Cloudflare Firewall to support containment and investigative actions

[comment]: # " File: readme.md"
[comment]: # "  Copyright (c) 2021 Splunk Inc."
[comment]: # ""
[comment]: # "  Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
## API Token

API Tokens provide a way to authenticate with the Cloudflare API and can be generated from the
[<span class="link"> User Profile 'API Tokens' page
</span>](https://dash.cloudflare.com/profile/api-tokens) . To support the available actions, please
assign the following permissions to your token:

-   `      Zone.Zone Settings     ` ,
-   `      Zone.Zone     ` ,
-   `      Zone.Firewall Services     `


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Cloudflare asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | Base URL for Cloudflare API \(e\.g\. https\://api\.cloudflare\.com/client/v4/\)
**api\_token** |  required  | password | API token to authenticate

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[block ip](#action-block-ip) - Block an IP  
[update rule](#action-update-rule) - Update a firewall rule  
[block useragent](#action-block-useragent) - Deny access to reported UserAgent  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'block ip'
Block an IP

Type: **contain**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** |  required  | IP to block | string |  `ip` 
**domain\_name** |  required  | Domain name \(exact match\) | string | 
**rule\_descr** |  optional  | Firewall rule name | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.domain\_name | string | 
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.parameter\.rule\_descr | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'update rule'
Update a firewall rule

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**rule\_name** |  required  | Firewall rule name \(case\-insensitive exact match\) | string | 
**domain\_name** |  required  | Domain name \(exact match\) | string | 
**action** |  required  | Action to apply | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.action | string | 
action\_result\.parameter\.domain\_name | string | 
action\_result\.parameter\.rule\_name | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'block useragent'
Deny access to reported UserAgent

Type: **contain**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**user\_agent** |  required  | UserAgent to block | string | 
**domain\_name** |  required  | Domain name \(exact match\) | string | 
**rule\_descr** |  optional  | Firewall rule name | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.domain\_name | string | 
action\_result\.parameter\.rule\_descr | string | 
action\_result\.parameter\.user\_agent | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 