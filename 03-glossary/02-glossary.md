# Glossary - all the terms, grouped by theme

> **In short:** each term has a plain meaning and, where useful, why it matters for Litra. The last column gives the Norwegian (NO) and Swedish (SE) word you may hear. More local words are on the [Nordic terms](03-nordic-terms.md) page.

## Business and roles

| Term | Plain meaning | Why it matters for Litra | NO / SE |
|---|---|---|---|
| **Haulier** (carrier) | Company that physically moves goods | Litra is the haulier | transportør / åkeri |
| **Shipper** (consignor) | Party sending the goods | Often a fuel or gas company, and usually the payer | avsender / avsändare |
| **Consignee** | Party receiving the goods | The delivery site, not always the payer | mottaker / mottagare |
| **3PL** | Third-party logistics provider | Litra is a specialised 3PL for liquids and gas | - |
| **Fleet Planner** | Person who plans and dispatches trips | Main user of the planning board | disponent, transportleder / transportledare |
| **Operating company** | Legal company inside the group | Each has its own currency, VAT, customers | selskap / bolag |
| **Secondary distribution** | Terminal to end customer, by road | Litra's core business | - |
| **Milk run** | One truck, many stops in sequence | Typical heating oil and gas route | - |
| **TMS** | Transport management system | What the platform is, in industry terms | - |
| **VMI** | Vendor-managed inventory: supplier refills based on tank levels | Future phase: orders from tank sensors | - |

## Fleet and planning

| Term | Plain meaning | Why it matters for Litra | NO / SE |
|---|---|---|---|
| **Tractor unit** | Truck head pulling a semi-trailer | Needs licence CE | trekkvogn / dragbil |
| **Semi-trailer** | Trailer whose front rests on the tractor | Most fuel tanks are semi-trailers | semitrailer / semitrailer |
| **Rigid truck** | Truck with its own tank body | Fits narrow city and farm sites | lastebil / lastbil |
| **Compartment** | Separate section of the tank | One product per compartment; drives the loading puzzle | kammer / fack |
| **Trip** | One truck and driver, loading and one or more stops | Unit of planning and of billing | tur / tur |
| **Time window** | When the customer accepts delivery | Late arrival is a warning, not a block | tidsvindu / tidsfönster |
| **Vehicle routing problem (VRP)** | Maths of finding the best set of trips | What the optimiser solves | - |
| **Hard rule / soft rule** | Never allowed / allowed with a reason | The base of explainable planning | - |
| **Override** | Planner accepts a soft-rule warning with a comment | Logged for audit | - |
| **Re-planning** | Changing a trip already under way | Delays, breakdowns, urgent orders | omplanlegging / omplanering |
| **Empty km** | Km driven with no cargo | Key cost and CO₂ driver | tomkjøring / tomkörning |
| **Utilisation** | How much each truck works | Core fleet KPI | utnyttelse / utnyttjande |
| **ETA** | Estimated time of arrival | Sent to customers automatically | - |

## Tank and products

| Term | Plain meaning | Why it matters for Litra | NO / SE |
|---|---|---|---|
| **Standard litres at 15 °C** | Volume corrected to a reference temperature | Fuel is traded and billed in it | standardliter / standardliter |
| **Observed litres** | Volume as measured at actual temperature | Must be converted before comparing | - |
| **VCF** | Volume correction factor, from industry tables | Turns observed into standard litres | - |
| **LPG** | Liquefied petroleum gas, mainly propane | Billed by kg; class 2 | propan / gasol |
| **LNG / LBG** | Liquefied natural gas / liquefied biogas, very cold | Special cryogenic tanks | - |
| **HVO** | Renewable diesel from vegetable oils and waste | Growing product in the Nordics | - |
| **Jet A-1** | Aviation fuel | Needs a dedicated trailer | jetdrivstoff / flygbränsle |
| **AdBlue** | Urea solution for diesel engines | Not dangerous, but must never touch fuel | - |
| **Bottom loading** | Filling the tank from below at the terminal | Standard, safer than top loading | bunnlasting / bottenlastning |
| **Dedicated trailer** | Trailer used for one product only | Jet fuel rule | - |
| **Meter** | Calibrated flow meter on the truck | Source of delivered quantity | måler / mätare |
| **Weighbridge** | Scale for weighing whole trucks | Source of quantity for gases | brovekt / fordonsvåg |
| **Extra operation** | Work beyond plain delivery: pump, long hose | Billed if the contract says so | - |

## Safety and compliance

| Term | Plain meaning | Why it matters for Litra | NO / SE |
|---|---|---|---|
| **ADR** | European agreement on dangerous goods by road | Governs almost every Litra trip | ADR / ADR-S |
| **Dangerous goods** | Products that can harm people or nature | Fuel, gas, chemicals | farlig gods / farligt gods |
| **Danger class** | One of 9 ADR groups (2 gases, 3 flammable liquids, 8 corrosives) | Decides tank, driver and route rules | - |
| **UN number** | Four-digit product code | On the orange plate and the waybill | UN-nummer / UN-nummer |
| **Hazard code** | Two or three digits above the UN number on the plate | Tells rescue services the danger type | farenummer / farlighetsnummer |
| **Packing group** | Danger level within a class (I high, III low) | Goes on the transport document | - |
| **Tunnel code** | Letters showing which tunnel categories a load must avoid | Routes must respect it; Norway has many tunnels | - |
| **ADR driver certificate** | Driver's dangerous goods training, valid 5 years | Expired means the driver is blocked | ADR-kompetansebevis / ADR-intyg |
| **Tank specialisation** | Extra ADR course for tank work | Required for all tank drivers | tankkurs / tankkurs |
| **ADR certificate of approval** | Yearly approval of a tank vehicle | Expired means the vehicle is blocked | - |
| **EU 561** | EU law on driving and rest times | Limits every plan | kjøre- og hviletid / kör- och vilotid |
| **Tachograph** | Device that records driving and rest | Source of remaining driving time | fartsskriver / färdskrivare |
| **Licence C / CE** | Truck licence / truck with heavy trailer | Must match the vehicle | førerkort / körkort |
| **Pre-trip check** | Walk-around safety check before driving | Recorded on the tablet | avgangskontroll / - |

## Documents

| Term | Plain meaning | Why it matters for Litra | NO / SE |
|---|---|---|---|
| **Transport order** | Customer's request for a delivery | Captured once, reused everywhere | transportoppdrag / transportorder |
| **Waybill, consignment note, CMR** | Legal document for the journey | Paper today, digital tomorrow | fraktbrev / fraktsedel |
| **e-CMR** | Electronic consignment note | Replaces paper; carries ADR details | - |
| **eFTI** | EU rule on electronic freight information | Authorities must accept it from July 2027 | - |
| **Loading document (BOL)** | Terminal's record of what was loaded | Trusted source for loaded quantity | - |
| **Manifest** | List of what is on board | Driver checks it against the order | - |
| **POD** | Proof of delivery | No POD, no invoice | kvittering / kvittens |

## Technology and integration

| Term | Plain meaning | Why it matters for Litra | NO / SE |
|---|---|---|---|
| **Telematics** | Truck sends its own data over mobile network | Real km, position, events | - |
| **rFMS** | Standard interface for truck data across brands | One integration for a mixed fleet | - |
| **CAN bus** | The truck's internal data network | Where km and fuel data originate | - |
| **Geofence** | Virtual boundary around a site | Proves arrival, departure and waiting | - |
| **Dwell time** | Time spent inside a geofence | Evidence for billed waiting | - |
| **EDI / EDIFACT** | Standard business messages between companies | How big customers send orders | - |
| **IFTMIN / IFTSTA / APERAK** | EDIFACT order / status / acknowledgement messages | The core EDI set for transport | - |
| **API / webhook** | Modern system interface / push notification | For newer customers and partners | - |
| **Master data** | Customers, sites, products, fleet, drivers | Foundation; bad master data breaks automation | grunndata / grunddata |
| **Offline-first** | App works without signal and syncs later | Tunnels and remote areas | - |
| **SSO** | Single sign-on with the company account | Staff log in once | - |
| **Role-based access** | Rights depend on role and company | Planners see only their company | - |
| **Event bus** | Channel that carries business events between parts | Makes the flow automatic and replayable | - |
| **Idempotent** | Safe to repeat; a retry never duplicates | Critical for invoice posting | - |
| **Audit log** | Record of who changed what, when | Overrides, prices, invoices | revisjonslogg / - |

## Finance and billing

| Term | Plain meaning | Why it matters for Litra | NO / SE |
|---|---|---|---|
| **Order to cash** | The full path from order to payment | The scope of the platform | - |
| **Reconciliation** | Comparing planned vs actual | Gate before automatic billing | avstemming / avstämning |
| **Tolerance** | Allowed difference before a trip is flagged | Decides how much is automatic | toleranse / tolerans |
| **Exception** | A trip outside tolerance | The only thing back-office reviews | avvik / avvikelse |
| **Contract** | Agreement with a customer | Points to the rate card, approval rules | kontrakt / avtal |
| **Rate card / tariff** | Price list: per m³, tonne, km, hour | Biggest estimation unknown | prisliste / prislista |
| **Zone** | Distance band from the terminal | Basis of volume and weight tariffs | sone / zon |
| **Surcharge** | Extra charge on top of the base price | Fuel, ADR, after-hours | tillegg / tillägg |
| **Waiting time** | Time lost queueing at terminal or site | Billed only if proven | ventetid / väntetid |
| **Invoicing basis** | Data used to build an invoice | What Excel holds today | fakturagrunnlag / fakturaunderlag |
| **Credit note** | Cancels a posted invoice fully or partly | Posted invoices are never edited | kreditnota / kreditfaktura |
| **ERP** | Enterprise resource planning system | UBW in Litra's case | - |
| **UBW / Unit4** | Litra's ERP (Unit4 Business World, formerly Agresso) | Stays; receives invoices | - |
| **Ledger** | Accounting record of all transactions | UBW keeps it | hovedbok / huvudbok |
| **EHF / PEPPOL** | Norwegian e-invoice format / European e-invoice network | How invoices are sent electronically | - |
| **VAT** | Value added tax | Differs per country | MVA / moms |
| **Credit block** | Finance stops new invoices to a customer | Causes UBW to reject posting | kredittsperre / kreditspärr |

## ESG

| Term | Plain meaning | Why it matters for Litra |
|---|---|---|
| **ESG** | Environmental, social, governance reporting | One of Litra's four evaluation pillars |
| **CO₂e** | All greenhouse gases expressed as CO₂ | The reported unit |
| **ISO 14083** | Standard for transport emissions | Credible numbers for customers |
| **GLEC Framework** | Industry method that follows ISO 14083 | Practical calculation guide |
| **Tonne-km** | One tonne moved one km | Fair basis to split emissions per customer |
| **Well-to-wheel** | Emissions from fuel production and burning | The usual reporting scope |
| **Biogas (LBG, CBG)** | Gas from organic waste, liquefied or compressed | Litra invests in biogas trucks |
