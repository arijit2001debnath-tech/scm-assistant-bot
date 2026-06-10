

<img width="662" height="521" alt="Screenshot 2026-06-10 171925" src="https://github.com/user-attachments/assets/bebb2546-d529-4862-9bc8-1158b9d5779d" />

🔹 LLM
Model: llama-3.1-8b-instant (Flowise node)
Provider: Groq
Purpose: Answer generation based on retrieved supplier data

<img width="684" height="343" alt="Screenshot 2026-06-09 211539" src="https://github.com/user-attachments/assets/6d1b5d72-3846-48af-b255-d3ddd108415f" />

🔹 Embeddings Model
Model: sentence-transformers/all-MiniLM-L6-v2
Provider: Huggingface
Purpose: Convert supplier CSV/text into vector representations for similarity search


<img width="1049" height="333" alt="Screenshot 2026-06-10 172006" src="https://github.com/user-attachments/assets/e673bcc4-0325-4cda-ab9f-8b1e12ca9ac0" />

🧩 Chunking Strategies Tried
✅ Chunk Config 1: No Splitting (Full Row / Document)
Strategy: Entire CSV row treated as a single chunk
Separator: None
Chunk size: Not applied

Result:

✔ Good for exact row-based retrieval
❌ Poor for semantic search across fields
❌ Limited flexibility for questions like performance trends
✅ Chunk Config 2: Recursive Character Text Splitter
Chunk Size: 1000 characters
Overlap: 200 characters
Separators: \n, ,, space hierarchy

Result:

✔ Better semantic retrieval
✔ Improved Q&A accuracy
✔ Works well for supplier performance queries
❌ Slight duplication in overlapping chunks


❓ Q&A Evaluation 
Q1

Question: Which Tier-3 suppliers have an active disruption flag, and what response level applies per policy?

Answer:Direct Answer: Tier-3 suppliers with an active disruption flag are subject to a Level 3 response.
Supporting Data:
According to the policy, a Level 3 response is triggered when a supplier has any disruption flag, or any supplier with two simultaneous disruption flags.
Since the question specifically asks about Tier-3 suppliers with an active disruption flag, we can infer that a Level 3 response is applicable.
The Level 3 response includes immediate escalation to the CPO, activation of an alternate supplier for a minimum of 40% of the volume within 10 business days, safety stock adjustment by +50%, and a full RCA required within 15 business days.
Final Summary: Tier-3 suppliers with an active disruption flag are subject to a Level 3 response, which includes immediate escalation to the CPO, activation of an alternate supplier, safety stock adjustment, and a full RCA. 


Q2

Question:Which suppliers qualify for the annual Volume Rebate Program and how many are there?

Answer:Direct Answer: Tier-1 suppliers qualify for the annual Volume Rebate Program
Supporting Data:
According to Section 4.2, Tier-1 suppliers with OTD at or above 93.0%, Defect Rate below 0.5%, and Sustainability Score at or above 85 for a full calendar year qualify for an annual volume rebate of 2.5% of total annual invoice value.
There is no specific information provided on the number of suppliers that qualify for the program.
Final Summary: Tier-1 suppliers qualify for the annual Volume Rebate Program, but the exact number of suppliers is not specified.


Q3

Question: Which region has the highest total PO value, and does it breach the concentration limit?

Answer:The total PO value for the EMEA region is $313486.34 (PO-11238) + $224562.52 (PO-10102) = $537948.86 (approx).
The concentration limit is not explicitly stated in the provided data.
However, we can infer that the concentration limit is likely related to the total annual volume or total PO value of a single region.
Based on the provided data, the EMEA region has the highest total PO value, but we cannot determine if it breaches the concentration limit without more information.
Final Summary: The EMEA region has the highest total PO value, but the concentration limit and its relation to the total PO value are not specified.


Q4

Question: Which suppliers are on Supplier Watch List (SWL) status and what does it restrict?

Answer:
Direct Answer: Suppliers with a Compliance Score below 60 at any audit are placed on Supplier Watch List (SWL) status.

Supporting Data:
Suppliers on SWL status are restricted from receiving new POs, with a limit of 20% of prior quarter volume.
The following suppliers are on SWL status:
SUP-005 (Compliance Score: 58)
SUP-012 (Compliance Score: 62, but has a lead time approaching the ELTRP review boundary)
SUP-015 (Compliance Score: 59)
SUP-023 (Compliance Score: 55)
Final Summary: Suppliers SUP-005, SUP-012, SUP-015, and SUP-023 are on Supplier Watch List (SWL) status due to a Compliance Score below 60. This restricts them from receiving new POs, with a limit of 20% of prior quarter volume


Q5

Question: Which product category has the highest average defect rate and does it exceed the Tier-2 limit?

Answer:Direct Answer: The product category with the highest average defect rate is Packaging Materials.

Supporting Data:
The average defect rate for Packaging Materials is 1.47% (based on PO-10455).
The Tier-2 limit for defect rate is 2.50%.
The average defect rate of 1.47% does not exceed the Tier-2 limit.
Final Summary: The product category with the highest average defect rate is Packaging Materials, but it does not exceed the Tier-2 limit of 2.50%.

