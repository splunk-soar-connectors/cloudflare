# Cloudflare

Publisher: Splunk Community <br>
Connector Version: 1.0.0 <br>
Product Vendor: Cloudflare <br>
Product Name: Cloudflare <br>
Minimum Product Version: 4.9.39220

This app integrates with Cloudflare Firewall to support containment and investigative actions

### Configuration variables

This table lists the configuration variables required to operate Cloudflare. These variables are specified when configuring a Cloudflare asset in Splunk SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base_url** | required | string | Base URL for Cloudflare API (e.g. https://api.cloudflare.com/client/v4/) |
**api_token** | required | password | API token to authenticate |
**verify_server_cert** | optional | boolean | Verify the Cloudflare server certificate |

### Supported Actions

[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration <br>
[block ip](#action-block-ip) - Block an IP <br>
[update rule](#action-update-rule) - Update a firewall rule <br>
[block useragent](#action-block-useragent) - Deny access to reported UserAgent

## action: 'test connectivity'

Validate the asset configuration for connectivity using supplied configuration

Type: **test** <br>
Read only: **True**

#### Action Parameters

No parameters are required for this action

#### Action Output

No Output

## action: 'block ip'

Block an IP

Type: **contain** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** | required | IP to block | string | `ip` |
**domain_name** | required | Domain name (exact match) | string | |
**rule_descr** | optional | Firewall rule name | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.domain_name | string | | |
action_result.parameter.ip | string | `ip` | |
action_result.parameter.rule_descr | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'update rule'

Update a firewall rule

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**rule_name** | required | Firewall rule name (case-insensitive exact match) | string | |
**domain_name** | required | Domain name (exact match) | string | |
**action** | required | Action to apply | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.action | string | | |
action_result.parameter.domain_name | string | | |
action_result.parameter.rule_name | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'block useragent'

Deny access to reported UserAgent

Type: **contain** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**user_agent** | required | UserAgent to block | string | |
**domain_name** | required | Domain name (exact match) | string | |
**rule_descr** | optional | Firewall rule name | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.domain_name | string | | |
action_result.parameter.rule_descr | string | | |
action_result.parameter.user_agent | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

______________________________________________________________________

Auto-generated Splunk SOAR Connector documentation.

Copyright 2026 Splunk Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and limitations under the License.
