# VIVIA PROPERTY OS v3

Multi-tenant rental operations system connecting:
Fillout → HubSpot → Stripe → TurboTenant Live Listings → Zite Database → Twilio SMS → Cal.com Scheduling

---

## 🌐 Core Domain

- Domain: VIVIARENTAL.COM
- Platform: https://testwpstaging.turbotenant.com/landlord-toolbox/lease-agreement-audit-ai/#
- System Type: Rental Operations OS + Employee Onboarding + Listing Syndication

---

## 🧠 System Architecture


Fillout Intake
↓
HubSpot CRM (Portal 147969685)
↓
Stripe Billing + Employee Activation
↓
Zite Database (Employees + Properties + Conversations)
↓
TurboTenant Live Listing Sync
↓
Marketing Syndication (Zillow / Zumper / External)
↓
Twilio + WhatsApp + SMS Alerts
↓
Cal.com Training + Onboarding Session


---

## 🔁 Unified Redirect Flow (Fillout → HubSpot → Stripe → TurboTenant)


fillout_session
→ hubspot_contact
→ stripe_customer
→ stripe_checkout_session
→ turbotenant_live_listing
→ zite_employee_activation
→ marketing_syndication


---

## 🔑 20-Key Reusable Redirect Parameters


email={{email}}
phone={{phone}}
first_name={{first_name}}
last_name={{last_name}}
city={{city}}
state={{state}}
country={{country}}
zip={{zip}}
role={{role}}
employee_id={{employee_id}}
client_reference_id={{client_reference_id}}
hubspot_deal_id={{hubspot_deal_id}}
stripe_customer_id={{stripe_customer_id}}
checkout_session_id={{CHECKOUT_SESSION_ID}}
property_id={{property_id}}
listing_id={{listing_id}}
signup_source={{signup_source}}
utm_source={{utm_source}}
utm_campaign={{utm_campaign}}
utm_medium={{utm_medium}}


---

## 💳 Stripe Employee Activation Link


https://testwpstaging.zite.so/employees?client_reference_id={{client_reference_id}}&email={{email}}&role=remote_property_manager


---

## 🏠 TurboTenant Live Listing Embed

```html
<html>
<body>
<iframe 
  style="border:none;"
  src="https://rental.turbotenant.com/embedpropertylist.html#/PROPERTY_ID_PLACEHOLDER"
  height="1240"
  width="100%">
</iframe>
</body>
</html>
📡 Webhook Routing System
TurboTenant
https://your-n8n.com/webhook/turbotenant-lead
Twilio SMS Inbound
https://your-n8n.com/webhook/twilio-inbound
HubSpot Lead Sync
https://your-n8n.com/webhook/hubspot-lead
🔐 API Authentication Headers
Zite API
Authorization: Bearer YOUR_ZITE_KEY
HubSpot API (EU Portal 147969685)
Authorization: Bearer YOUR_HUBSPOT_TOKEN
Twilio
Account SID + Auth Token (via n8n node)
🧑‍💼 Employee Onboarding Flow (V2)
Step 1 — Fillout Intake
Collect employee profile
Assign role (Remote Property Manager)
Step 2 — HubSpot Creation
Contact + Deal created
Pipeline Stage = "Onboarding"
Step 3 — Stripe Activation
Customer created
Checkout session generated
Employee redirected to:
Stripe Billing Portal
Step 4 — TurboTenant Assignment
Property assigned
Listing synced
Status = Live
Step 5 — Zite Employee Record
Employee ID generated
Conversation + task routing activated
Step 6 — Cal.com Training
https://cal.com/turbo-rentals/tenant-landlord-services
📊 Service Offer Options
Rental Management
Payment Processing
Scheduling (Tours + Onboarding)
Employee Onboarding System
📲 SMS Alert System
Publish Code Format
SMS Logged — Publish Code: 676788
Status: Sent → Queued → Delivered
🧾 Custom Event Payload (Onboarding JSON)
{
  "workflow_version": "vivia-rentals-v2",
  "environment": "production",
  "automation": {
    "stripe_redirect": true,
    "hubspot_sync": true,
    "turbotenant_sync": true,
    "sms_verification": true
  },
  "integrations": {
    "stripe": "bpc_1TaPNUDI5ZfGRQdNl8QFpcs7",
    "hubspot": "147969685",
    "turbotenant": "active",
    "zite": "enabled"
  }
}
🔄 Multi-Tenant Routing Rules
Condition	Action
Renter	Tour scheduling + SMS invite
Landlord	Listing onboarding
Employee	Stripe activation + training
Lead	HubSpot + Zite sync
🚀 Final System Behavior
All leads are captured instantly
Employees are auto-assigned
Stripe activates onboarding access
TurboTenant listings go live automatically
Twilio sends SMS confirmations
HubSpot tracks full lifecycle
🏁 Production Status
Environment: Production Ready
Version: v3
Deployment: Active
Domains: VIVIAPROPERTY.COM
May 27, 03:11:05 PM: [AR]-[cleanup_stage] Successfully uploaded cumulative_diff to S3May 27, 03:11:05 PM: [AR]-[cleanup_stage] Updating agent runner with cumulative diff S3 keyMay 27, 03:11:05 PM: [AR]-[tracing] ⏳ TRACE: update-runner starting...May 27, 03:11:05 PM: [AR]-[tracing] ✅ TRACE: PUT completed in 89.69ms [http.request.method=PUT, url.full=https://api.netlify.com/api/v1/agent_runners/6a1740e222fcd4bc561d6e27, url.host=api.netlify.com, url.scheme=https, server.address=api.netlify.com, server.port=, http.response.status_code=200]May 27, 03:11:05 PM: [AR]-[api] Request ID for https://api.netlify.com/api/v1/agent_runners/6a1740e222fcd4bc561d6e27: 9b97f08b-72bb-4b28-82e2-32716587ef73May 27, 03:11:05 PM: [AR]-[tracing] ✅ TRACE: update-runner completed in 90.87msMay 27, 03:11:05 PM: [AR]-[cleanup_stage] Updated agent runner with resultMay 27, 03:11:05 PM: [AR]-[tracing] ⏳ TRACE: update-runner-session starting...May 27, 03:11:06 PM: [AR]-[api] Request ID for https://api.netlify.com/api/v1/agent_runners/6a1740e222fcd4bc561d6e27/sessions/6a1740e222fcd4bc561d6e29: 786611f5-2ddd-47ff-a75f-21836b4c5856May 27, 03:11:06 PM: [AR]-[tracing] ✅ TRACE: PUT completed in 510.59ms [http.request.method=PUT, url.full=https://api.netlify.com/api/v1/agent_runners/6a1740e222fcd4bc561d6e27/sessions/6a1740e222fcd4bc561d6e29, url.host=api.netlify.com, url.scheme=https, server.address=api.netlify.com, server.port=, http.response.status_code=200]May 27, 03:11:06 PM: [AR]-[tracing] ✅ TRACE: update-runner-session completed in 512.01msMay 27, 03:11:06 PM: [AR]-[cleanup_stage] Finished updating agent runner with resultMay 27, 03:11:06 PM: [AR]-[tracing] ✅ TRACE: cleanup-stage completed in 738.49msMay 27, 03:11:06 PM: HEAD is now at c3dcbd7 Agent runnerMay 27, 03:11:06 PM: [AR]-[tracing] ✅ TRACE: run-pipeline completed in 225916.48msMay 27, 03:11:06 PM: [AR]-[bin_cmd] Finished agentMay 27, 03:11:06 PM: Finished processing dev server in 3m50.017sMay 27, 03:11:06 PM: ==================================================================May 27, 03:11:06 PM:
