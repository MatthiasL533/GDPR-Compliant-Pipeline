# GDPR-Compliant-Pipeline

Here is the brief information about the the GDPR-compliant Pipeline( This is not the final version!).
* Initial Dataset Upload:
    * The user uploads the dataset.
* Data Processing Module:
    * Attributes like name and passport number, which can directly identify an individual, are dropped.
    * Assessment of Missing Data: Columns with missing data are evaluated for the percentage of missing values.
    * Decisions are made on whether to remove columns based on their utility and informativeness.
    * Identification of Quasi-Identifiers for the first round of data generalisation.
    * Dataset is partitioned into equivalence classes (ECs) based on quasi-identifier combinations.
    * Quasi-identifiers’ distinct values and distribution percentages are assessed.
    * Values are mapped or grouped to minimize distinct values within each quasi-identifier.
    * The updated dataset is forwarded to the subsequent privacy processing module

* GDPR-Compliant Privacy Metric Module:
    *K-Anonymity: Identifies the value of k required in each ECs.
    *Normalised Entropy l-Diversity: Calculate the normalised entropy for each sensitive attribute.
    *Average the mean of the normalised entropy values across all sensitive attributes.
    *Calculat t-Closeness and apply Min-Max normalisation to each t value.
    *Calculate the mean of these normalised t values across all sensitive attributes.
    *Establish a permissible boundary for t-values (should not exceed 0.5).
    *P_29 Score Calculation: A scoring mechanism to denote overall privacy level termed as P29 Score.
            *Incorporates k-Anonymity, l-Diversity, and t-Closeness metricsl;
            *Assign weights to each metric (k-Anonymity: 0.5, l-Diversity: 0.25, t-Closeness: 0.25);
            *Establish conditions for kmin, l, and t values to avoid critical privacy risks.
            *Making P_29 Score is directly proportional to data privacy.
* Privacy Processing Module:
    *Datasets with a P29 Score of 0 undergo data deletion.
    *Adding noise to the data using differential privacy to further anonymize it: Once the desired privacy metrics are achieved, proceed to another privacy module;Adding noise to the data using differential privacy to further anonymize it.
    *Sequence of deletion prioritizes t-closeness, followed by k-anonymity and l-diversity.
    *Ensure ECs do not contain only one record or a single dominant value.
    *Local Differential Privacy: Apply noise to exact values within non-sensitive attributes to improve privacy.
            *Numerical attributes perturbed using the Laplace mechanism.
            *Categorical columns protected using the randomized response mechanism.
    *Parameters include Sensitivity and Epsilon for controlling privacy-accuracy trade-off.
     
In summary, it safeguards datasets by mitigating three major privacy risks. Techniques include k-anonymity, l-diversity, t-closeness, and local differential privacy.
This combination of techniques were also recommended to address various identification risks in WP216.

