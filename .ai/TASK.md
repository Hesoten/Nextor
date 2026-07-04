The previous commit (12931fccf0e9d3bc4f60ac405f57efa4d571def2) upgraded the existing Nextor 2.0 documeneation for Nextor 3.0 (notably, the user manual, the programmers reference, and the driver developer guide). Your job is to do the following tasks:


## 1. Fix stuff and fill the gaps

Read the changed documents and do the following:

- Fix typos and grammar mistakes as you find them.

- Review the numbering and leveling of the makrdown titles, then fix the invalid ones; notably, there are now duplicate numberings as new sections have been added without renumbering the existing sections.

- Once all the titles are fixed, rebuild the indices at the top of the documents.

- Search the `TODO:` markers and follow the instructions. Most of these (but not all) are missing anchors to other sections in the same and in other documents.

- Fix the text of anchors where it makes sense, e.g. `see [the "foobar" section]` could be `see _[X.Y.Z Foobar]_`.

- With the help of the resources listed below, verify the validity of the documents:
  - Do all the changes accurately reflect how Nextor 3 works?
  - Is something missing?
  - Is there obsolete information (which was true for Nextor 2 but doesn't apply to Nextor 3) still in place?
  - Is there any duplication that makes sense to remove?


## 2. Write the what's new guide

The `docs/Nextor 3.0 What's New.md` file already exists but it's empty. This file is intended for people who is already familiar with Nextor 2 but new to Nextor 3. It should have two main sections:

- General information/features that everybody (users and developers) should be aware of. Things like "there's a new driver system" (without detailing the technical details, but mentioning things like "no more LUN support" or "no more drive-based drivers"), "support for floppy disks" or "boot menu", amongst others. New BASIC CALL commands and CLI tools should be mentioned too.

- Information for application programmers: new function calls, changes to existing function calls (including the ones that were already existing in MSX-DOS 2, e.g. `_FORMAT`), new error codes, the SDK, and any other relevant information.

The document shouldn't go into full detail for any of the points it mentions, instead it should link to the corresponding section of the corresponding document where appropriate. Briefly mention also that for driver developers there's a dedicated document: the driver migration guide (see below).


## 3. Write the driver migration guide

The `docs/Nextor 3.0 Driver Migration Guide.md` file already exists but it's empty. This file is intended for people who created a driver for Nextor 2 and want to adapt it to Nextor 3.

The main tone of the document should be "most of your existing code can be reused by adding a compatibility layer" (exactly what was done for e.g. the Sunrise IDE driver) and it should take the form of a step-by-step guide, e.g. "1. Replace the driver header, 2. Rename the existing routines, 3. Add this code..."


## Resources

Information you can use to guide the process:

- The diff of commit 12931fccf0e9d3bc4f60ac405f57efa4d571def2 (originally the docs were for Nextor 2).

- https://github.com/Konamiman/Nextor/pulls?q=sort%3Aupdated-desc+is%3Apr+project%3Akonamiman%2F3+state%3Amerged+ as the list of pull requests that shaped Nextor 3. Note that most of the ones whose title has a `[Nextor 3]` prefix are backports of features/fixes that were incorporated into Nextor 2 (while the `v3.0` branch evolved separately) but verify for each case.

- The Sunrise IDE driver for v3 (~/NextorDrivers/SunriseIDE) vs the driver for v2 (https://github.com/Konamiman/Nextor/tree/v2.1/source/kernel/drivers/SunriseIDE) as an example of a driver migrated via compatibility layer.

- The new standalone driver (source/drivers/standalone-rom-driver.asm) vs the Nextor 2 equivalent (https://github.com/Konamiman/Nextor/tree/v2.1/source/kernel/drivers/StandaloneASCII8) for the differences in the driver structure.

- source/drivers/ram-driver-example.asm as an example of a RAM driver.

- ~/NextorDrivers/TurboR-FDD as an example of a driver that can be compiled for ROM or for RAM.

- The full source code of Nextor itself (this repo, this branch) whenever needed.


## Other guidelines for the task

- Start by gathering as much information as you can so that you can ask me all your questions upfront and then work uninterrupted.

- When/where it makes sense, try to parallellize the work using multiple agents.

- Leave all the changes in the working tree, don't commit or push anything.
