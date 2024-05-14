# GDPR-Compliant-Pipeline

Here is the brief information about the the GDPR-compliant Pipeline( This is not the final version!).
* Initial Dataset Upload:
    * The user uploads the dataset.
* Data Processing Module:
    * Uploader select identifiers to delete.
    * Select the attributes to delete due to missing value
    * Select the attributes as the quasi-identifier
    * Generalizes or suppresses data based on the distribution of selected quasi-identifier values throughout the dataset.
* Privacy Metric Module:
    * Identifies the minimum value of k required to achieve k-anonymity.
    * Provides warnings regarding which equivalence classes and which variables fail to meet:
        * k-anonymity: the rows with the same combination of quasi identifier
        * Entropy l-diversity: Ensures sensitive attributes have sufficient diversity.
        * t-closeness: Controls the difference between the sensitive attribute distribution within an equivalence class and the global distribution.
* Privacy Processing Module:
    * If the data does not meet the specified k-anonymity, the user can return to the data processing module. OR, achieving through data suppression 
    * Under the data suppression , the amount of data loss will be given
    * Adjustments are made to achieve the desired entropy l-diversity and t-closeness.
* Further Privacy Module (Differential Privacy):
    * Once the desired privacy metrics are achieved, proceed to another privacy module.
    * Adds noise to the data using differential privacy to further anonymize it.
