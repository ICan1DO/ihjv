## Step 1:

Line 1

```
name: Task_Name # Task name
```

Line 25

```
- name: Task_Name # Task name
```

Task_Name -> You give this task a name.

## Step 2:

Line 5

```
- cron: 'Cron_expression' # Execution time
```

Cron_expression -> The time of task execution, modified here to Cron expression.

- You can read this [documentation](https://github.com/chiupam/tutorial/blob/master/Loon/Plus/cron.md) to learn how to write cron expressions.

## Step 3:

Line 29

```
source_repo: "Git_Address" # Git address of this repository
```

Git_Address -> Modify it to the git address you need to synchronize.

- sample: https://github.com/chiupam/Notes.git

## Step 4:

Line 30

```
source_branch: "Git_Branch" # Branch of this repository
```

Git_Branch -> Modify it to the branch you need to synchronize.

- sample: main

## Step 5:

Line 31

```
destination_branch: "Your_Branch" # Create your own branch
```

Your_Branch -> Create a new branch of your own.