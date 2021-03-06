validation
==========

This repository contains all files related to validation of the simplerinvoicing XML files.

If you are just looking for the latest validation artefacts in xsl form, you can find them here:

* [SI-UBL Invoice all versions up to 1.2](xsl/si-ubl-inv-all.xsl)
* [SI-UBL 1.1 Invoice](xsl/si-ubl-1.1.xsl)
* [SI-UBL 1.2 Invoice](xsl/si-ubl-1.2.xsl)
* [SI-UBL 1.2 Purchase Order](xsl/si-ubl-1.2-purchaseorder.xsl)
* [SI-UBL 2.0 Invoice and CreditNote (2.0.3)](xsl/si-ubl-2.0.xsl)
* [SI-UBL 2.0 G-Account extension (1.0)](xsl/si-ubl-2.0-ext-gaccount.xsl)

Note that we have removed the 'all-versions' schematron.

Versioning
==========

Since this repository contains multiple versioned validation sets, the versioning of the repository through it tags is separate from the versions of the validation sets themselves.

Versioning of the validation artefacts uses the major.minor.bugfix approach; Major and minor versions are updated if the specification itself changes, bugfixes are only updates of the validation artefacts when issues are found.

The repository uses a single version by date approach; any time one or more validation sets are updated into a release, the repository version changes to the current date, e.g. 2020-02-14. See the Changelog file for the mapping of repository releases and validation set releases. The links above always refer to the latest version of each set.

Directory overview
==================

The ready-to-use transformation stylesheets can be found in the xsl/ directory; there is a separate xsl file for each version of SI-UBL, and one big xsl-file that combines them all (si-ubl-inv-all.xsl). For SI-UBL 1.2, there is also a purchaseorder xsl.

The schematron/ directory contains all the source schematron files, also by version. The main sch files are present in this directory, and they reference files in subdirectories per version.

The rule_overviews/ directory contains a few assorted documents, and overview of the rules per version, generated from the xsl files.

The tools/ directory contains the tools to recreate the xsl files from the schematron files. For instance, to create a fresh SI-UBL-1.2 xsl file, you can use the command:
    ./tools/convert_linux.sh schematron/si-ubl-1.2.sch /tmp/si-ubl-1.2.xsl

The build_all_linux.sh script rebuilds all generated files in this repository, based on the schematron files.


SI-UBL 2.0.3
============

This is the version of SI-UBL that is based on the NLCIUS, which is a CIUS on the European Norm (EN-16931) and adds Dutch country-specific rules.

Since this is based on EN-16931, there are major differences between SI-UBL 1.2 and SI-UBL 2.0. For more information about the new rules, see https://www.stpe.nl/media/stpe.nl-gebruiksinstructie-basisfactuur-v1.0.pdf

The schematron can be found [here](schematron/si-ubl-2.0.sch) and the generated xsl [here](xsl/si-ubl-2.0.xsl)

This schematron definition is based on the CenPC434 schematron, which can be found at https://github.com/CenPC434/validation . The commit that was included at the time of the release of SI-UBL-2.0.3 was https://github.com/CenPC434/validation/commits/fa4c0abb1 (tag validation-1.3.1), with one additional proposed fix, shown in https://github.com/tjeb/eInvoicing-EN16931/commit/5e5e39ffe39f64d0496c717f6c471365d5d7cc4c

Test Files
==========

We have a number of test documents available in a separate repository, it can be found [here](https://github.com/SimplerInvoicing/testset)
