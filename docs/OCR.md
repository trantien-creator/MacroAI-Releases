# OCR

MacroCanvas supports OCR steps for reading visible text from a Windows application or Android emulator capture.

## OCR engines

- Windows OCR can use the automatic Windows language profile.
- Windows OCR can be configured for Vietnamese or English.
- Tesseract data for `vie` and `eng` is included for supported recognition flows.

## Region selection

A smaller region is usually faster and produces fewer unrelated characters.
Pixel-based OCR regions depend on the target resolution, DPI, aspect ratio, and orientation.
Recheck every OCR region after moving a workflow to a different environment.

## Improving results

- Capture sharp text at a stable scale.
- Avoid animated backgrounds when possible.
- Keep the region close to the expected text.
- Choose the correct language.
- Normalize UI scaling between workflow creation and execution.
- Test both expected and missing-text conditions.

## Limitations

OCR output can vary with font rendering, antialiasing, transparency, contrast, and motion.
A successful result in one environment does not guarantee the same result after a UI update or resolution change.
Use retries, validation, and safe-stop branches for unattended workflows.

## Privacy

OCR runs locally against captured target content.
Review screenshots and logs before sharing them because recognized text may contain private information.

[Back to English README](../README.md) · [Về README tiếng Việt](../README.vi.md)
