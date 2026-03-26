skills:
  - name: classify_complaint
    description: Classifies a single complaint description into category, priority, reason, and review flag.
    input: A dictionary representing one complaint row containing at least complaint_id and description fields.
    output: A dictionary with keys complaint_id, category, priority, reason, and flag.
    error_handling: If description is missing, null, or ambiguous, assigns category "Other", sets priority to "Low" or "Standard", and marks flag as "NEEDS_REVIEW".

  - name: batch_classify
    description: Reads a CSV file of complaints, applies classify_complaint to each row, and writes results to an output CSV file.
    input: Path to input CSV file containing complaint records.
    output: Output CSV file containing classified complaints with category, priority, reason, and flag fields.
    error_handling: If a row fails processing, it logs the failure, assigns category "Other", sets priority to "Low", and continues processing remaining rows without crashing.