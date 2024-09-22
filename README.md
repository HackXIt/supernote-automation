# supernote-automation
A repository holding several tools and implementations, that I like to use or work with for automation purposes.

# Purpose

I usually like to use my supernote for taking notes on all kinds of things, but mostly I take notes during classes and meetings. The latter are notes which I also need to process regularly to do additional work.
All of my notes are synced to OneDrive and I have the desire to just have my notes exported/moved auto-magically, to continue working on them outside of the supernote.
However, I don't want to manually do this for each individual note, but I also do not want to do it for ALL the notes. I want to have a way to configure how the notes are processed and where they are moved/exported to.

## Pre-conditions

These pre-conditions apply to MY use-case and should help differentiate the requirements from YOUR use-case.

- Note taking folder structure
    - I organize my notes in a hierarchical structure, meaning there's a folder for work, folder for studying, folder for personal, etc.
    - I add additional folders in that structure, depending on the needs of the topic (e.g. a subfolder for a course, a subfolder for a project, etc.)
    - This also means, I need some sort of mapping to decide what to do with the folders (i.e. include them in the processing or not)
- Special processing for used templates
    - Sometimes notes might use a specific PDF template, where I'll need to map the template with a processing configuration for that specific template. The default should be regular notes (i.e. regular export, no extraction).
    - For those special templates, I'd like to have the feature to extract specific information from the notes and process them accordingly.
    - This special processing should be configurable (opt-in)
    - The special processing should be configurable for each template (i.e. different processing for different templates)
    - The purpose of the processing should be to extract additional information to be used in Obsidian for further work (e.g. extracting tasks, extracting questions, etc.)
- Exporting notes and processing for further work
    - I have a homelab setup, where I can run docker containers and scripts to process the notes automatically.

## Workflow

0. OneTime Setup
    - Create a configuration for my supernote usage (folder-structure, mappings for how to process folders, mappings for how to process subfolders, mappings for how to process templates, etc.)
1. Supernote usage
    - Take notes in the supernote
    - Sync the supernote to OneDrive
2. Processing
    - Worker node detects changes in supernote folder
    - Worker runs a script to process the notes in the OneDrive folder (only new notes)
    - The script will:
        - Read the configuration
        - Read the notes
        - Process the notes according to the configuration
        - Export the notes to a suitable format (e.g. Obsidian)
        - Move the exports to the configured processed folder
3. Continue work in Obsidian

# Project Tasks

- [ ] Create a supernote PDF template, which later is used by machines to extract information in specific sections via OCR or similar.
- [ ] Create a worker program (docker container), which will detect changes in OneDrive and gather NEW notes to be processed.
- [ ] Create a configuration structure, which will hold the configuration for the worker. (preferably yaml)
- [ ] Create a script, which will automatically export NEW notes found in OneDrive to PDF/other configured formats.
- [ ] Create a script, which will gather notes from the synced folder and create vault notes in Obsidian for them.