---
title: Resume
icon: material/certificate
tags:
- About
- Resume
- Contact
- Work
---

<style>
    ul li {line-height: 1.4}
    ol li {line-height: 1.2}
</style>

## :material-magnify-scan: Validate

Send my resume file below to verify its origin and status, using a local hash check:

<!-- Genuine -->
<div class="file-genuine" style="display: none" markdown>

!!! success "_Genuine File • I hereby certify that I am the author of this file, and that:_"

    - :material-lock: Not a single byte has been modified, added or removed from the original.
    - :octicons-law-16: The contents were truthful at the time of generation, and likely still hold.
    - :material-recycle: Only I could have created and issued this file to be distributed.

    <small><b>Filename:</b> <span class="filename"></span></small>

</div>

<!-- Invalid -->
<div class="file-invalid" style="display: none" markdown>

!!! warning "Invalid File • Possible reasons, from best to worst case:"

    - :fontawesome-solid-user: **Mistake**: Wrong upload, check the filename below - it happens.
    - :octicons-sync-16: **Syncing**: I forgot to update the valid files list or deploy to the website.
    - :material-file-edit: **Modified**: An optimization or post-processing step altered it needlessly[^modified].
    - :material-ghost: **Forgery**: Contents were tampered with, and should not be trusted.

    -> Please contact me directly to investigate and/or provide a new copy.

    <small><b>Filename:</b> <span class="filename"></span></small>

[^modified]: Such as stripped metadata, compression, or added text, tags, and watermarks - accept cautiously.

</div>

<!-- Stale -->
<div class="file-stale" style="display: none" markdown>

!!! warning "Stale - Certain parts may be significantly outdated or incorrect."

</div>

<!-- Input -->
<input type="file" id="file-upload" accept="application/pdf" hidden>
<label class="md-button" for="file-upload">
    :octicons-upload-16: Validate File
</label>

<!-- Logic -->
<script>
    const originalHashes = [];
    const recalledHashes = [];

    document.getElementById("file-upload").addEventListener("change", async (input) => {
        const file = input.target.files[0];
        if (!file) return;

        const genuineDiv = document.querySelector(".file-genuine");
        const invalidDiv = document.querySelector(".file-invalid");
        const staleDiv   = document.querySelector(".file-stale");

        // Will show a new result
        genuineDiv.style.display = "none";
        invalidDiv.style.display = "none";
        staleDiv.style.display   = "none";

        try {
            const digest = await crypto.subtle.digest("SHA-256", await file.arrayBuffer())

            // Convert raw bytes to hex string
            const hash = Array.from(new Uint8Array(digest)).map(
                b => b.toString(16).padStart(2, "0")
            ).join("").toLowerCase();

            // Origin check
            if (originalHashes.includes(hash)) {
                genuineDiv.style.display = "block";
            } else {
                invalidDiv.style.display = "block";
            }

            // Status
            if (recalledHashes.includes(hash)) {
                staleDiv.style.display = "block";
            }

        } catch (error) {
            alert("Error computing file hash: " + error);
        }

        // Update visible filenames display
        document.querySelectorAll(".filename").forEach(element => {
            element.textContent = file.name;
        });
    });
</script>

## :material-file-check: Request

For privacy and data protection reasons, you can email me a resume request for manual review, and I'll send a custom file with relevant information for the position on a good-faith basis.

-> Simply send an email to [resume@tremeschin.com](mailto:resume@tremeschin.com), following the guidelines below:

### Guidelines

For strengthtening our trust relationship, please:

- :material-account-check: **Include** a copy of your resume too (preferable), company and profile names I can search and unambiguously verify, relevant job openings, anything proving identity.
- :material-chat-processing: **Describe** the general area of interest, how you found about me, work type, etc.
- :material-web-off: **External** links and trackers will not be seen, attach images and files directly.
- :material-text-short: **Direct** and human text, corporate speak, Ai and syncophancy are auto-ignored.

<small>
    <b>Note</b>: Failing to meet the criteria above may result in a rejection, ghosting or blocking.
</small>

### Content

Made with [Typst](https://typst.app/) on a modern and elegant presentation:

- :fontawesome-solid-user: **Personal**: Name, age, location, contact, positions of interest, abstract, others.
- :fontawesome-solid-graduation-cap: **Academic**: Bachelor's degree and final paper, scientific initiation and research, tutoring, weighted grade point average[^gpa], and all their links/certificates/validators.
- :fontawesome-solid-users: **References**: People who can vouch for you, their contact information and positions.
- :fontawesome-solid-code: **Code**: Best projects, languages, current stars, description, age, and links.
- :fontawesome-solid-star: **Skills**: Spoken languages, technical and soft skills, interests, and others.

[^gpa]: **Note**: In :flag_br: Brazil, the scale is from 0 to 10, simply multiply by 0.4 for :flag_us: USA equivalence.

<small><b>Note</b>: I may send a partial document when in doubt about legitimacy.</small>
