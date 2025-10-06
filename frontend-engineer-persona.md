# Frontend Engineer Persona - Troubleshooting with Grafana Cloud

## Scenario: Investigating Production Errors

### Step 1: Check Frontend Observability Dashboard
**Alert triggered → jump into the frontend dashboard.**

We receive an alert indicating issues with the frontend application. Navigate to Grafana Cloud Frontend Observability to begin investigation.

![Frontend Observability Dashboard](image_assets/frontend_observability_dashboard.png)

### Step 2: Error Spike Detected
**Breakdown highlights specific pages impacted.**

In the main overview, we observe increased errors affecting the application. 

![Frontend Observability Overview](image_assets/frontend_observability_overview.png)

Looking at the page performance panel view to see a breakdown of which pages are affected. We discover that only certain pages are experiencing issues.

![Frontend Page Breakdown](image_assets/frontend_page_breakdown.png)

### Step 3: Product View
**Critical failure state clearly visible.**

Let's navigate to the product page where errors are concentrated. Click on the row in the Page Performance panel that has '/product/*' in the first column. The product page shows only errors - a critical situation requiring immediate attention.

![Frontend Product Page Details](image_assets/frontend_product_page_details.png)

### Step 4: User Session Replay
**Multiple API recommendation errors identified.**

Select an individual user session to see the complete details of that user's journey and understand their experience. Within the user session, we find multiple errors related to the API recommendation endpoint.

![Frontend Session Overview](image_assets/frontend_session_overview.png)

![Frontend Session Details](image_assets/frontend_session_details.png)

![Frontend Session Details Error](image_assets/frontend_session_details_error.png)

### Step 5: Trace Analysis
**Drill in to see error originates from the recommendation service.**

Click on the HTTP request and navigate to traces. The distributed trace reveals the full request path. The trace shows the error originating from the recommendation service. The span details contain the specific error message.

![Frontend Traces](image_assets/frontend_traces.png)

![Frontend Trace Explain in Assistant](image_assets/frontend_trace_explain_in_assistant.png)

### Step 6: Service Catalog Lookup
**Escalate to on-call team with trace context.**

We are not the owner of the recommendation system, but it's impacting our frontend application. Look up the recommendation service in the service catalog to find the on-call team. Share the conversation from the assistant trace explanation with the recommendation service team to help them quickly understand and resolve the issue.

![Frontend Trace Share Analysis](image_assets/frontend_trace_share_analysis.png)
![Frontend Service Center](image_assets/frontend_service_center.png)
![Frontend Service Center Escalate](image_assets/frontend_service_center_escalate.png)
