Version: NAFATH-V2

Your track: Networking

Overview

‫ Emergency responders need a reliable 5G service when many people use the network, equipment fails, or cyber attacks occur. Software design helps services handle requests safely and recover from temporary errors. Artificial intelligence can predict network congestion and help operators prepare before performance drops. Mobile applications should keep essential information available offline and synchronize updates when the connection returns. Networking provides connectivity and manages traffic so that emergency communications receive suitable priority. Cybersecurity helps teams detect attacks, limit damage, and restore services safely. Data modeling supports daily reports by region, helping managers understand usage and identify weak areas. These six fields work together to support reliable emergency communication. For this project, 5G network slicing is the networking approach considered for prioritizing emergency traffic

Software

HTTP methods have two important properties: safety and idempotency. GET, HEAD, OPTIONS, and TRACE are safe because they are intended to read information without changing the server’s state. These methods are also idempotent. PUT and DELETE are idempotent because repeating the same request has the same intended effect. This matters when a client retries a failed request. Repeating an idempotent request is generally safer than repeating a POST request, which may create duplicate actions.

Resource: RFC 9110: HTTP Semantics - https://www.rfc-editor.org/rfc/rfc9110.html

AI

‫ Overfitting happens when a model learns its training data too closely, including noise, and performs poorly on new data. Cross-validation helps detect this by training and testing the model on different parts of historical data. If the model performs well during training but poorly during validation, it may not generalize well. The operator should also test it on recent, unseen network data before using its congestion predictions in real operations

Resource: 3.1. Cross-validation: evaluating estimator performance - https://scikit-learn.org/stable/modules/cross_validation.html


Mobile

A responder’s mobile app should keep essential information available locally when the network is unavailable. It should clearly show when information may be out of date. Updates that can safely wait should be saved in a local queue. When connectivity returns, the app should synchronize these updates, retry temporary failures, and resolve conflicts using clear rules. Actions that require live server confirmation must remain clearly marked as unavailable until the server confirms them.

Resource: Build an offline-first app - https://developer.android.com/topic/architecture/data-layer/offline-first

Networking

5G network slicing creates multiple logical networks on shared physical infrastructure. Each slice can be configured for different service needs, such as bandwidth, latency, and security. The operator could provide emergency responders with a dedicated slice designed to prioritize critical traffic and support reliable communication during congestion. However, slicing alone cannot prevent every outage. Capacity planning, continuous monitoring, security controls, and backup connections are still needed to keep the service dependable.

Resource: Network Slicing - https://www.gsma.com/solutions-and-impact/technologies/networks/5g-network-technologies-and-solutions/5g-standalone-networks/network-slicing/

Cybersecurity

‫ Incident response includes preparing for incidents, detecting and analyzing threats, containing their impact, removing the cause, and recovering services. When an attack occurs, the operator should identify affected systems, isolate compromised components when necessary, and preserve evidence. The team should remove the threat, restore trusted systems, check that services work correctly, and monitor for further attacks. Afterward, a review should identify lessons and improve security controls and response plans

Resource: SP 800-61 Rev. 3, Incident Response Recommendations and Considerations for Cybersecurity Risk Management - https://csrc.nist.gov/pubs/sp/800/61/r3/final

Data

A star schema uses a central fact table connected directly to dimension tables, such as date and region. A snowflake schema splits some dimensions into additional related tables to reduce repeated descriptive data. However, this creates more joins and can make reports harder to use. For daily service-usage reports by region, a star schema is usually simpler. Its fact table can store usage totals linked to date and region dimensions.

Resource: Understand star schema and the importance for Power BI - https://learn.microsoft.com/en-us/power-bi/guidance/star-schema

Misconception in My Track

A common misconception is that a dedicated 5G network slice is a completely separate physical network and guarantees communication during every outage. In reality, network slicing creates logical networks that can share physical infrastructure. Each slice can be configured to meet different service requirements, including latency, bandwidth, and security. However, shared infrastructure can still fail, and coverage problems can still occur. The operator must also plan capacity, monitor performance, and provide backup arrangements. The GSMA resource explains this under the heading “What is Network Slicing?”

Resource: Network Slicing - https://www.gsma.com/solutions-and-impact/technologies/networks/5g-network-technologies-and-solutions/5g-standalone-networks/network-slicing/

 Open Question

‫ I would verify the operator’s latency, availability, and coverage targets for emergency responders and test whether the dedicated slice can meet them during congestion and a major network failure
