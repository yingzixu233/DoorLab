# DoorLab

DoorLab helps designers explore interior door layouts inside Autodesk Revit. Starting from modeled walls and rooms, it generates candidate door positions, checks opening clearances, and compares validated plans with a design-cost breakdown. Select a plan to place its doors and passage openings in the model, including hinge side and swing direction.

[Download the installer and examples](https://github.com/yingzixu233/DoorLab/releases) · [Quick start](QUICKSTART.md)

![DoorLab benchmark reference layout](docs/images/floorplan_1_reference.png)

This benchmark image is generated from the original Notebook sample JSON.

The current pre-release includes a Windows x64 build for Revit 2026 using .NET 8. Validation used Revit API file version 26.0.10.8. Revit 2026.5 and later updates use .NET 10 and require a matching DoorLab build. The release asset list and release notes identify the included build. [Autodesk runtime compatibility guidance](https://www.autodesk.com/support/technical/article/caas/sfdcarticles/sfdcarticles/Compatibility-and-performance-considerations-when-running-different-versions-of-Revit-together.html)

## Install and run

Close Revit, download `DoorLabSetup.exe`, and double-click it. The setup window detects Revit installations and selects compatible versions. Click **Install**, then **Finish**. Reopen Revit and find **DoorLab - Export Floorplan** and **DoorLab - Plan Door Layout** under **Add-Ins → External Tools**. The installer includes the solver and its Python dependencies. This pre-release installer is unsigned, so Windows may display a publisher confirmation.

The settings window has four pages. **Openings & Clearances** selects family types, widths and clearances. **Layout Rules** controls the circulation start and bathroom fallback. **Scoring** edits circulation preferences and room-connection costs. **Search Settings** controls position sampling and the search budget. Question-mark buttons provide field explanations. Length inputs accept feet, inches, feet-and-inches, millimeters, centimeters and meters. The selected family type supplies the actual width used by the solver.

Click **Generate Plans** to solve in the background and open **Compare Door Plans**. Lower design cost is better. **Score Breakdown** shows each cost contribution. The search considers a finite set of sampled positions, opening directions and hinge sides. A complete search enumerates all equal-best plans in that candidate set. An incomplete search shows the validated equal-best plans found within the search budget.

## Model scope

This version works with one floor-plan scope, an unrotated rectangular exterior, straight basic walls, and one closed boundary loop per room. Supported room names include `Living`, `Kitchen`, `Bedroom 1` and `Bathroom 1`, with corresponding Chinese names. Unassigned regions are excluded from the circulation model. Clearance checks use room boundaries, opening approach strips and door sweeps. Furniture and other equipment require additional designer review.

## Examples

The separate `DoorLab_Examples_Revit2026.zip` download contains three blank Revit models with tested family types loaded. Each model has its own folder, such as `Floorplan_1/Floorplan_1_blank.rvt`. Start with `EXAMPLES_GUIDE.md` in the archive, or read the [examples guide](docs/EXAMPLES_GUIDE.md) online.

The accompanying reference PNGs are benchmark layouts generated from the original Notebook sample JSON. [ReferenceSettings.json](docs/ReferenceSettings.json) records their settings. Revit export coordinates, geometry details, actual family widths and equal-cost alternatives can affect the resulting layout and score. Use the Revit-generated preview to verify the doors applied to your model.

For feedback, include the full Revit build number, selected family types and widths, relevant settings, and steps to reproduce the issue.
