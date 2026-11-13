# DoorLab example models for Revit 2026 and 2027

Start from a doorless working copy with suitable wall-hosted swing-door and passage-opening types loaded. DoorLab v0.1.1 includes Revit 2026 / .NET 8 and Revit 2027 / .NET 10 builds in one installer. Use the build that matches your Revit release and update. Revit 2026.5 and later updates require a separate Revit 2026 / .NET 10 build, which is outside this package.

Each sample is in its own folder so DoorLab can create a separate revit-exchange folder beside that model.

Download `DoorLab_Examples_Revit2026.zip` for Revit 2026, or `DoorLab_Examples_Revit2027.zip` for Revit 2027. Each archive contains three models saved in the named Revit format. Revit 2026 cannot open the 2027 models.

Make a working copy of an entire sample folder before testing. If using the 2026 archive in Revit 2027, allow Revit to upgrade the copied model and save the upgraded copy before exporting. Keep the original 2026 files.

| Sample | Test focus |
|---|---|
| Floorplan 1 | First run, settings, scores and application |
| Floorplan 3 | Irregular rooms, hinge sides and swing directions |
| Floorplan 6 | More complex room connections and unassigned area |

## Run a sample

1. Close all Revit windows and run the v0.1.1 DoorLab installer. Select the available Revit 2026 or 2027 version, install, then reopen Revit. Extract the matching examples ZIP to a writable local folder and copy the sample folder you want to test. Open the copied model and its floor-plan view containing the named rooms. Save the upgraded copy if opening a 2026 model in Revit 2027.
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

MANIFEST.json records the model format and checksums for the files in the archive, together with reference-calculation provenance. The reference results above validate the original Notebook JSON benchmarks; they do not establish identical scores or per-model verification for the supplied Revit files. Saved working copies have different file contents and checksums.
