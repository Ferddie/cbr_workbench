# CBR Workbench

A browser-based case-based reasoning (CBR) tool for research and teaching. Upload an Excel knowledge bank of past cases, set a weight for each attribute, describe a new case, and retrieve the most similar past cases with their similarity in percent. Results can be downloaded as an Excel report.

No programming and no installation are needed. Everything runs in your browser: your Excel file is read on your own computer and is not uploaded to any server.

**Open the tool:** `https://<your-username>.github.io/cbr-workbench/`

## How to use it

1. **Knowledge bank.** Choose a built-in sample, or upload your own `.xlsx` file. The first sheet must have one header row and one past case per row.
2. **Criteria and weights.** The tool detects each column as numeric or categorical. Pick the solution column (the outcome to reuse), then set a weight from 0 to 100 for each attribute.
3. **New case.** Enter the values of the new problem.
4. **Most similar cases.** Choose how many cases to show (top N). Each case shows its global similarity and the local similarity of every attribute. Use **Download results (.xlsx)** for the full report.
5. **Revise and retain.** Confirm or adapt the suggested solution, click **Add to knowledge bank**, then **Download updated knowledge bank (.xlsx)** to keep the new case.

## How similarity is calculated

| Attribute type | Local similarity |
|---|---|
| Categorical | 1 if the values are equal (case and extra spaces ignored), otherwise 0 |
| Numeric | 1 − \|a − b\| ÷ range, where the range includes the new case's value |

Global similarity = Σ (weight × local similarity) ÷ Σ weights, shown as a percentage. A blank stored value scores 0. Ties keep the order of the file.

## Sample knowledge banks

The `samples` folder holds Excel files you can download and use as templates:

| File | Cases | Description |
|---|---|---|
| [`oman_tourism_cases.xlsx`](samples/oman_tourism_cases.xlsx) | 80 | Synthetic Oman tour packages: travel party, group size, age, origin market, season, interest, budget, trip length, accommodation, package taken |
| [`tourist_spot_example.xlsx`](samples/tourist_spot_example.xlsx) | 5 | The workshop's manual calculation example: choosing a tourist spot |
| [`dam_gate_example.xlsx`](samples/dam_gate_example.xlsx) | 4 | Classic dam gate example from the CBR lecture |

The tourism data are synthetic and for training only.

## Requirements

A current version of Chrome, Edge, Firefox or Safari, with an internet connection. The page loads the ExcelJS library from the jsDelivr CDN and its fonts from Google Fonts.

## Author

Dr. Ferddie Quiroz Canlas, Muscat University. Prepared for the workshop *From Past Cases to Future Destinations: Applying AI in Tourism Research*, Oman Tourism College.

CBR cycle after Aamodt, A. and Plaza, E. (1994). Case-based reasoning: foundational issues, methodological variations, and system approaches. *AI Communications*, 7(1), 39–59.
