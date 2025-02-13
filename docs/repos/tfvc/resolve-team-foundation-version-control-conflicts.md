---
title: Resolve Team Foundation Version Control conflicts
titleSuffix: Azure Repos
description: Resolve Team Foundation Version Control conflicts
ms.assetid: 61cae295-0864-4ae9-8327-9bd1dd14cae9
ms.technology: devops-code-tfvc
ms.topic: conceptual
ms.date: 07/13/2022
monikerRange: '<= azure-devops'
---


# Resolve Team Foundation Version Control conflicts

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)]
[!INCLUDE [version-vs-gt-2013](../../includes/version-vs-gt-2013.md)]


An advantage of using Team Foundation version control to manage your files is that several people can work concurrently on a file. One drawback is that sometimes you must resolve conflicts before you can get, check in, unshelve, merge, or roll back your files.

Although it can be frustrating to encounter conflicts, the system provides information and tools to help you understand and resolve conflicts.

<a name="manage_items"></a>

## Resolve conflicts

Use the Resolve Conflicts window to resolve conflicts that are blocking you.

:::image type="content" source="media/resolve-team-foundation-version-control-conflicts/IC745580.png" alt-text="Use the Resolve Conflicts window to resolve conflicts.":::

:::image type="content" source="media/resolve-team-foundation-version-control-conflicts/IC612247.png" alt-text="Resolve conflicts":::

By default, the window shows only the conflicts caused by the most recent operation you attempted. When the window is in this state, a message appears that begins: **Path filter applied**. To show all conflicts in your workspace, choose **Get All Conflicts**. A message that begins with: **n Conflict(s)** appears.

If a lot of time has passed since you made changes to files in your workspace, new conflicts might have occurred. To refresh the **Resolve Conflicts** window, choose **Refresh**.

Each conflict contains information and sometimes links that might help you resolve it. To get more information, you can select the conflict and choose:

-   ![Choose History.](media/resolve-team-foundation-version-control-conflicts/IC277131.png) **History** to see the history of the file. If the operation that caused the conflict is a Merge or a Rollback, then you can choose the menu control to the right of **History** and then select either **Source History** or **Target History**.

    See [Get the history of an item](get-history-item.md).

-   ![Choose Annotate.](media/resolve-team-foundation-version-control-conflicts/IC277132.png) **Annotate** to view details on all changes that were made to the most recent version of the file, including who made each change and when they made it. See [View file changes using annotate](view-file-changes-using-annotate.md).

-   ![Choose Compare.](media/resolve-team-foundation-version-control-conflicts/IC277133.png) **Compare** (or the menu to the right of the button and then choose a command). The [Diff](compare-files.md) window appears.

<a name="autoresolve"></a>

## AutoResolve all conflicts

By default the system automatically attempts to **AutoResolve All** conflicts unless you have turned off this option (see [Tips](resolve-team-foundation-version-control-conflicts.md#tips)). In the Resolve Conflicts window, you can also manually choose **AutoResolve All**, and then choose:

-   Select **All Conflict Types** if you want the system to attempt to resolve the conflicts automatically by using all its heuristics.

-   Select **Specific Conflict Types** if you want the system to attempt to resolve the conflicts, but you want to exclude some heuristics.

    The **Choose Conflicts to Resolve** dialog box appears. Check or clear the options that you want to enable or disable, and then choose **AutoResolve**. For more information, see [Understand the automatic options](resolve-team-foundation-version-control-conflicts.md#automatic_options) below.

The system attempts to automatically resolve the conflicts displayed in the Pending Changes window. Any conflicts the system was unable to resolve will remain in the window. You have to [manually resolve](resolve-team-foundation-version-control-conflicts.md#manual) these conflicts.

<a name="automerge"></a>

## AutoMerge a single conflict

Choose **AutoMerge** if you want to try to resolve selected conflicts using all the AutoMerge options described in [Understand the automatic options](resolve-team-foundation-version-control-conflicts.md#automatic_options) below.

> [!TIP]
> You can press and hold either the Ctrl or the Shift key and then select multiple conflicts.
>
> [!NOTE]
> If **AutoMerge** is disabled, then this conflict must be [manually resolved](resolve-team-foundation-version-control-conflicts.md#manual).

<a name="manual"></a>

## Manually resolve a single conflict

If the system cannot automatically resolve a conflict, or if you want to make sure you understand what is changing, you must manually resolve the conflict. Within each conflict, the system displays the actions that you can take to resolve the conflict. The actions displayed depend upon the conflict type, and the operation that caused the conflict.

### Merge changes in merge tool

When a conflict is caused by conflicting content changes, you can choose **Merge Changes in Merge Tool**.

When you choose this action, the Merge window appears.

:::image type="content" source="media/resolve-team-foundation-version-control-conflicts/IC612248.png" alt-text="Merge changes in merge tool":::

The outcome of your work to resolve the conflict is shown in the **Results** pane.

In this window you can:

-   Select the layout of the window: **Vertical View**, **Horizontal View**, **Mixed View**.

-   Navigate among the differences and the conflicts.

-   Select items from the left and right versions of the file to include them in the result.

-   Type additional content into the file in the Result pane.

-   View the History of the file. See [Get the history of an item](get-history-item.md).

-   Compare the various versions of the file.

-   Annotate the file to see who changed what. See [View file changes using annotate](view-file-changes-using-annotate.md).

When are satisfied with the contents of the **Result** pane, choose **Accept Merge**.

<a name="automatic_options"></a>

## Understand the automatic options

In special cases, you may want to restrict the types of conflicts automatically resolved by the **AutoResolve All** option.

When you choose **AutoResolve All**, and then **Specific Conflict Types**, the **Choose Conflicts to Resolve** dialog box appears.

:::image type="content" source="media/resolve-team-foundation-version-control-conflicts/IC612249.png" alt-text="Understand the automatic options":::

:::row:::
   :::column span="1":::
   **If you want the system to automatically resolve conflicts that occurred because...**
   :::column-end:::
   :::column span="1":::
   **As explained in this example...**
   :::column-end:::
   :::column span="1":::
   **Then select this check box...**
   :::column-end:::
:::row-end:::
---
:::row:::
   :::column span="1":::
   Non-conflicting content changes were made in each version of a file
   :::column-end:::
   :::column span="1":::
   In the file version on the left, a **zero** was added at the beginning. In the file on the right, a **three** was added at the end:

   ![Non-conflicting content changes](media/resolve-team-foundation-version-control-conflicts/IC377394.png)
   :::column-end:::
   :::column span="1":::
   **Conflicts with any content changes**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   Content changes were made that are unique to the workspace (during get or checkin operation) or target version (during merge or rollback operation)
   :::column-end:::
   :::column span="1":::
   **four** and **five** were added to the workspace or target version:

   ![Content changes unique to workspace or target](media/resolve-team-foundation-version-control-conflicts/IC377395.png)
   :::column-end:::
   :::column span="1":::
   **Conflicts with content changes made only in the local workspace or target branch**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   Content changes were made that are unique to the server (during get or checkin operation) or source version (during merge or rollback operation)
   :::column-end:::
   :::column span="1":::
   **four** and **five** were added to the server or source version:

   ![Content changes unique to server or source](media/resolve-team-foundation-version-control-conflicts/IC377396.png)
   :::column-end:::
   :::column span="1":::
   **Conflicts with content changes made only in the server version or source branch**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   A file on the server (during get or checkin operation) or in the source branch (during merge or rollback operation) was renamed
   :::column-end:::
   :::column span="1":::
   You checked out a file that is named **launch.cs** and worked on it. During that time, someone else checked in a changeset that affected the same file. That changeset did not modify the contents of the file, but it did change the name of the file to **start.cs**.
   :::column-end:::
   :::column span="1":::
   **Conflicts caused by renaming file in the server version or source branch**
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
   
   - Common content changes were made that resulted in identical content in each version

   - You changed a file, checked it in through a Gated Check-in build, and selected the **Preserve my pending changes locally** option

   
   :::column-end:::
   :::column span="1":::
   Changes to each version resulted in identical file content. The changes can be to the content in the files, as shown in the following example:

   ![Identical content changes in each version](media/resolve-team-foundation-version-control-conflicts/IC377397.png)
   This option also resolves conflicts that are caused by all other operations (for example, rename, delete, undelete, and branch) and that result in identical files.

   > [!Tip]  
   > If you select this check box, when you proceed, the system will resolve these changes by taking (downloading) the server version onto your workspace.
   :::column-end:::
   :::column span="1":::
   **Conflicts caused by identical change in the server and workspace**
   :::column-end:::
:::row-end:::


<a name="command_prompt"></a>

## Work from the command prompt

-    [Resolve Command](resolve-command.md) 

## Tips

-   ![Tips](media/resolve-team-foundation-version-control-conflicts/IC572374.png) By default the system automatically attempts to **AutoResolve All** conflicts. To change the option, from the menu bar choose **Tools**, **Options**, and then in the **Options** dialog box, navigate to **Source Control**, **Visual Studio Team Foundation Server**. Clear the **Attempt to automatically resolve conflicts when they are generated** checkbox.

-   ![Tips](media/resolve-team-foundation-version-control-conflicts/IC572374.png) Does your team need to collaborate to resolve a large number of conflicts (for example, which might occur after merge operation in a large codebase)? If so, a public workspace on a shared dev machine might help. See [Create and work with workspaces](create-work-workspaces.md).
