# DoorLab example models for Revit 2026

These three doorless models provide test starts with the tested wall-hosted swing-door and passage-opening families loaded. Use the released DoorLab build that matches your Revit update. The current installer contains the Revit 2026 / .NET 8 build.

Each sample is in its own folder so DoorLab can create a separate revit-exchange folder beside that model.

| Sample | Test focus |
|---|---|
| Floorplan 1 | First run, settings, scores and application |
| Floorplan 3 | Irregular rooms, hinge sides and swing directions |
| Floorplan 6 | More complex room connections and unassigned area |

## Run a sample

1. Extract this entire examples ZIP to a writable local folder. Open one sample model in Revit 2026 and open its floor-plan view containing the named rooms.
2. Run **Add-Ins > External Tools > DoorLab - Export Floorplan**. Select the four exterior basic walls when prompted. The walls define the rectangular exterior outline used by this prototype.
3. Open **DoorLab - Plan Door Layout**. Choose the loaded swing-door and passage-opening family types by their actual widths. Family and type names can follow the language of the model.
4. To compare against the benchmark settings, choose a swing-door width of **3 ft / 36 in / 914.4 mm** and an archway width of **4 ft / 48 in / 1219.2 mm**. Use **Reset to Defaults** for the remaining settings, then select the family types. ReferenceSettings.json records all benchmark settings and connection costs.
5. Click **Generate Plans**. When the comparison window opens, inspect the preview, openings, score breakdown and measurements. Lower design cost is better. The window identifies a search that stopped before all equal-best plans were enumerated.
6. Select a plan and click **Apply Selected Plan**. Check positions, hinges and swing directions in plan and 3D. Use Revit **Undo** to restore the doorless test start before trying another plan.

The reference images and benchmark JSON files were generated with the current solver from the original Notebook floorplan dictionaries. They illustrate one validated optimal solution for those benchmark inputs. Actual Revit exports can have different coordinates, dimensions, wall spans or equal-cost choices, so record the exported inputs and chosen family widths when comparing runs. The plugin enumerates equal-best plans within its finite candidate set and configured time budget.

The JSON files under each sample folder document the reference calculation. DoorLab writes its own active-model exports in revit-exchange when you run **Export Floorplan**.

Floorplan 6 includes unassigned space. Unlabelled voids are excluded from circulation in this prototype. Its reference demonstrates the supplied room graph and geometry.

## Reference results

| Benchmark | Openings | Design cost | Validation |
|---|---:|---:|---|
| Floorplan_1 | 4 | 11.850000 | Passed |
| Floorplan_3 | 5 | 14.870000 | Passed |
| Floorplan_6 | 6 | 22.950000 | Passed |

MANIFEST.json records model-copy checksums, solver and Notebook checksums, settings and validation results. The model version is Revit 2026. Revit files saved by a newer release require a compatible Revit version.
