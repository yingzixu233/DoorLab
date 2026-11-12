# Try DoorLab in Revit 2026

Download `DoorLabSetup.exe` and `DoorLab_Examples_Revit2026.zip` from the [release page](https://github.com/yingzixu233/DoorLab/releases). Close Revit, double-click the installer, and click **Install** for an available Revit version. After installation, reopen Revit.

1. Extract the examples into a writable local folder. Read `EXAMPLES_GUIDE.md`, then open `Floorplan_1/Floorplan_1_blank.rvt` and its floor-plan view. Keep the supplied folder structure so each example has a separate `revit-exchange` directory.
2. Run **Add-Ins → External Tools → DoorLab - Export Floorplan**. Select the four exterior walls when prompted. These walls define the rectangular outer boundary for this example.
3. Run **DoorLab - Plan Door Layout**. On **Openings & Clearances**, select the example's loaded swing-door type and passage-opening type. Check **Actual Width Used** for each selection. Use `ReferenceSettings.json` when you want to compare the settings used for the benchmark drawings.
4. Review the other three settings pages. Hover over a **?** for a short explanation, or click it for more detail. A width such as `3 ft`, `36 in` or `914.4 mm` represents the same length.
5. Click **Generate Plans**. The progress window reports candidate generation, search and preview rendering. Use **Cancel** to stop a run. When generation finishes, **Compare Door Plans** opens automatically.
6. Select a plan from the list. Inspect its preview, **Openings**, **Score Breakdown**, and **Measurements**. Check the hinge side and swing direction in the selected preview.
7. Click **Apply Selected Plan**. Inspect the result in plan and 3D views. Use Revit's Undo command to return to the blank layout before applying another plan.

Use `Floorplan_3/Floorplan_3_blank.rvt` after the first example to examine irregular room shapes. `Floorplan_6/Floorplan_6_blank.rvt` provides a more complex room arrangement and unassigned space. Benchmark images are available for [Floorplan 1](docs/images/floorplan_1_reference.png), [Floorplan 3](docs/images/floorplan_3_reference.png), and [Floorplan 6](docs/images/floorplan_6_reference.png).

These PNGs are generated from the original Notebook sample JSON with the recorded reference settings. A Revit export may use different coordinates or geometry details, and the selected family widths and equal-cost alternatives can affect the result. Compare the applied doors with the preview generated for your Revit model.

For a controlled scoring check on Floorplan 1, record Plan 1's cost breakdown, change **Scoring → Room Connection Costs → Public Room to Public Room** from `1` to `2`, and generate again. Inspect the **Kitchen / Living | Room connection** contribution and compare the total with the reference settings. Family width, geometry and all other settings should match when comparing runs.

If DoorLab reports that previews and settings differ, use **Generate Plans** for the current settings. After editing walls or room boundaries, export the active floor plan again before generating. A search marked incomplete means the time budget ended before equal-best enumeration finished.

Revit 2026 sample files should be opened with a compatible Revit 2026 installation. The installer lists the versions that match its included build. Save separate model copies for testing other Revit releases.
