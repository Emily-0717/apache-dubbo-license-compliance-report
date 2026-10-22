# Apache Dubbo License Compliance Report

A five-page license compliance assessment of **Apache Dubbo 3.3.6**, produced for the "Open Source Compliance and Licenses" course assignment.

## Report

- [Word report](report/apache-dubbo-3.3.6-license-compliance-report.docx)
- [PDF version](report/apache-dubbo-3.3.6-license-compliance-report.pdf)

## Scan evidence

- [Trivy HTML report](scan/trivy-license-report.html)
- [Raw Trivy JSON](scan/trivy-license-results.json)

## Scan summary

| Item | Result |
|---|---|
| Target | Apache Dubbo 3.3.6 source release |
| Tool | Trivy 0.76.1 (`--license-full`) |
| Files in source tree | 4,758 files / about 19.06 MB |
| License records | 3,981 records across 3,979 files |
| Licenses | Apache-2.0 (3,972 Java files), MIT (3 Java files), BSD-3-Clause (1 Java file) |
| Strong copyleft | None detected (no GPL / AGPL / SSPL) |
| Key gap | `ProtoTypeMap.java` declares BSD-3-Clause by reference only; Trivy missed it. Add the full BSD-3-Clause text and fix the broken `LICENSE.txt` reference. |

## Scope and caveats

- The scan covers the source tree. `pom.xml` files were skipped after Maven Central returned HTTP 429, so Maven transitive dependencies are not included.
- Runtime dependency risk is discussed separately in the report using the project's `.licenserc.yaml` (67 declared dependencies, including 6 CDDL and 6 EPL).
- This repository is for coursework and is not legal advice.

## Reproducing the scan

```bash
trivy fs --scanners license --license-full --offline-scan \
  --skip-files "**/pom.xml" --format json \
  --output trivy-license-results.json <dubbo-source-dir>
```

The HTML report was generated from the raw JSON with a small Python script; the Word report was built with `python-docx` and exported to PDF with LibreOffice.

## Main references

- Apache Dubbo: https://dubbo.apache.org/
- Apache License 2.0: https://www.apache.org/licenses/LICENSE-2.0
- Trivy License Scanning: https://trivy.dev/latest/docs/scanner/license/
- Apache Dubbo 3.3.6 source release: https://archive.apache.org/dist/dubbo/3.3.6/apache-dubbo-3.3.6-src.zip
