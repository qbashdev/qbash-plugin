---
name: qbash
description: Use when the person asks to automate a job, build or change a qbash task, run a task and read its result, look something up in their qbash memories, or use an app they connected in qbash.
---

# Working with qbash

qbash runs automations called tasks. A task is a script that qbash builds from a plain description and saves to the person's qbash account, where it can run on a schedule or on request. Every tool works with the person's own qbash permissions, in the organization they picked when they signed in. Results that change something carry an `app_url`, the page in qbash for it. Give that link to the person.

## Build a task

1. Look for an existing task first with `list_tasks`, passing `query` to narrow the list. `read_task` shows what a task does and which inputs it takes.
2. Call `build_task` with a message that says what the task should do, which inputs it takes and where its results go. It returns a `session_id`.
3. Follow the build with `check_build` and the `session_id`. When the builder asks a question, show it to the person and send their reply back through `build_task` with `answer`.
4. When the build is saved, the result carries the `task_id`.

## Run a task and read the result

1. Call `run_task` with the task's id and its inputs. It returns an `execution_id`.
2. `get_task_result` waits for the run to finish and returns its output. `get_task_log` shows the run's steps and any error.
3. `list_task_runs` lists earlier runs of a task.

## Change a task

`revise_task` changes a saved task, including its schedule or webhook. For a task the person did not build in this conversation, the first change answers with a link where the person allows edits to it, for a time they choose. Give them the link, then call `revise_task` again. `run_tests` runs the task's tests with connected apps mocked, and `check_build` with the returned `job_id` reads the result.

## Memories

`list_memory_folders` lists the folders the person can use. `grep_memories` searches documents and `read_memories` reads them. `write_memories` creates documents and `edit_memories` changes them. Some folders need a person to accept each change, and the result says when a change is waiting for review.

## Connected apps

`list_connectors` shows the apps the person connected in qbash and the accounts for each. For an app they have not connected, `request_connector` returns a link where they connect it in qbash. Never ask the person for passwords or API keys. `describe_connector` lists an app's operations and says whether each one reads or writes. `call_connector_read` runs an operation that reads and `call_connector_write` runs one that changes data. The first call for an account answers with a link where the person allows it.

## Help

`contact_qbash` sends a question, bug report or feature request to the qbash team, who reply to the person.
