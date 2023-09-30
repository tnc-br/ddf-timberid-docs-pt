# ⁉ Import Errors



<table><thead><tr><th width="167.33333333333331">Error</th><th>Description</th><th>How to Fix</th></tr></thead><tbody><tr><td>__ column is required</td><td>Caused when an expected column is not found in the csv. Required columns are: <br>- code<br>- trusted<br>- lat<br>- lon</td><td>Add the required column to the CSV file</td></tr><tr><td>trusted value should be one of the following: known, uncertain, or unknown</td><td>Caused if a value in the "trusted" column is not equal to "known", "uncertain", or "unknown"</td><td>Make sure all values in the trusted column are one of the required values</td></tr><tr><td>__ should be within the range __ and __</td><td>Caused when a value is outside of the expected range.</td><td>Make sure all values are within the specified range. </td></tr></tbody></table>
