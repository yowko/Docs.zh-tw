---
title: 作法：建立循序工作流程
description: 本文所建立的工作流程會使用這兩個內建活動，例如 Sequence 活動和自訂活動。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 0c47290d11770a094fb09bcb4dc34aee1e4371a9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190516"
---
# <a name="how-to-create-a-sequential-workflow"></a>作法：建立循序工作流程

工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題逐步解說如何建立工作流程，此工作流程會使用活動等內建活動 <xref:System.Activities.Statements.Sequence> ，以及先前的 how [To：建立活動](how-to-create-an-activity.md) 主題的自訂活動。 此工作流程會以數字猜測遊戲為模型。

> [!NOTE]
> 「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成 [如何：建立活動](how-to-create-an-activity.md)。

## <a name="to-create-the-workflow"></a>建立工作流程

1. 以滑鼠右鍵按一下 **方案總管** 中的 **[numberguessworkflowactivities]** **，然後選取 [** 新增]、[**新增專案**]。

2. 在 [ **已安裝** 的 **一般專案** ] 節點中，選取 [ **工作流程**]。 從 **[工作流程]** 清單中選取 **[活動]**。

3. `SequentialNumberGuessWorkflow`在 [**名稱**] 方塊中輸入，然後按一下 [**新增**]。

4. 從 [**工具箱**] 的 [**控制流程**] 區段，將 [ **Sequence** ] 活動拖放到工作流程設計介面上的 [在 **此放置活動**] 標籤。

## <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數

1. 按兩下 **方案總管** 中的 [ **SequentialNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。

2. 在工作流程設計工具的左下方按一下 [ **引數** ]，以顯示 [ **引數** ] 窗格。

3. 按一下 **[建立引數]**。

4. 在 `MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [加入]，從 [**引數類型**] 下拉式清單 **中** 選取 [ **Int32** ]，然後按 enter 儲存引數。

5. 按一下 **[建立引數]**。

6. 在 `Turns` 新加入之引數底下的 [**名稱**] 方塊中輸入 `MaxNumber` ，從 [**方向**] 下拉式清單 **中** 選取 [從自 **變數類型**] 下拉式清單選取 [ **Int32** ]，然後按 enter 鍵。

7. 在活動設計工具的左下方按一下 **[引數]**，以關閉 **[引數]** 窗格。

8. 在工作流程設計工具的左下方按一下 [ **變數** ]，以顯示 [ **變數** ] 窗格。

9. 按一下 **[建立變數]**。

    > [!TIP]
    > 如果沒有顯示 [ **建立變數** ] 方塊，請按一下工作流程設計工具介面上的 [ **Sequence** ] 活動加以選取。

10. 在 `Guess` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。

11. 按一下 **[建立變數]**。

12. 在 `Target` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。

13. 在活動設計工具的左下方按一下 **[變數]**，以關閉 **[變數]** 窗格。

## <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動

1. 從 [**工具箱**] 的 [**基本**] 區段中，將 [**指派**] 活動拖放到 [**序列**] 活動上。 在 `Target` [ **到** ] 方塊中輸入，並在 [ **輸入 c # 運算式** ] 或 [ **輸入 VB 運算式** ] 方塊中輸入下列運算式。

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > 若 **[工具箱]** 視窗並未顯示，請從 **[檢視]** 功能表中選取 **[工具箱]**。

2. 從 [**工具箱**] 的 [**控制流程**] 區段中，將 [ **DoWhile** ] 活動拖放到工作流程上，使其位於 [**指派**] 活動下方。

3. 在 [ **DoWhile** ] 活動的 [ **條件** ] 屬性值方塊中輸入下列運算式。

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <xref:System.Activities.Statements.DoWhile> 活動會執行其子活動，然後評估其 <xref:System.Activities.Statements.DoWhile.Condition%2A>。 如果 <xref:System.Activities.Statements.DoWhile.Condition%2A> 判斷值為 `True`，則會再次執行 <xref:System.Activities.Statements.DoWhile> 中的活動。 此範例中會評估使用者的猜測，而 <xref:System.Activities.Statements.DoWhile> 會繼續，直到猜測正確為止。

4. 從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段拖曳 [**提示**] 活動，然後將它放在上一個步驟的 [ **DoWhile** ] 活動中。

5. 在 [**屬性] 視窗** 的 [ `"EnterGuess"` **提示**] 活動的 [ **BookmarkName** ] 屬性值方塊中，輸入包含引號。 `Guess`在 [**結果**] 屬性值方塊中輸入，並在 [ **Text** ] 屬性方塊中輸入下列運算式。

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > 如果未顯示 [**屬性] 視窗**，請從 [ **View** ] 功能表選取 [**屬性視窗]** 。

6. 從 [**工具箱**] 的 [**基本**] 區段中，將 [**指派**] 活動拖放到 [ **DoWhile** ] 活動中，讓它遵循 [**提示**] 活動。

    > [!NOTE]
    > 當您卸載 [ **指派** ] 活動時，請注意工作流程設計工具如何自動加入 [ **Sequence** ] 活動，以同時包含 [ **提示** ] 活動和新加入的 [ **指派** ] 活動。

7. 在 [到] 方塊中輸入 `Turns` ，然後 `Turns + 1` 在 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入。

8. 從 [**工具箱**] 的 [**控制流程**] 區段中，將 [ **If** ] 活動拖放到 [**序列**] 活動中，使其在新增的 [**指派**] 活動之後。

9. 在 [ **If** ] 活動的 [ **條件** ] 屬性值方塊中輸入下列運算式。

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. 從 [**工具箱**] 的 [**控制流程**] 區段中，將另一個 [ **if** ] 活動拖放到第一個 [ **if** ] 活動的 [ **Then** ] 區段中。

11. 在新加入的 [ **If** ] 活動的 [ **條件** ] 屬性值方塊中輸入下列運算式。

    ```text
    Guess < Target
    ```

12. 將兩個 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **If** ] 活動的 [ **Then** ] 區段中，另一個則是在 [ **Else** ] 區段中。

13. 按一下 [ **Then** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。

    ```text
    "Your guess is too low."
    ```

14. 按一下 [ **Else** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。

    ```text
    "Your guess is too high."
    ```

     下列範例說明已完成的工作流程：

     ![顯示已完成之連續工作流程的螢幕擷取畫面。](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a>若要建置工作流程

1. 按 CTRL+SHIFT+B 建置解決方案。

     如需如何執行工作流程的指示，請參閱下一個主題 [：如何：執行工作流程](how-to-run-a-workflow.md)。 如果您已經完成 how to：使用不同的工作流程樣式來[執行工作流程](how-to-run-a-workflow.md)步驟，而且想要使用此步驟中的順序工作流程來執行它，請直接跳至 how [To：執行工作流程](how-to-run-a-workflow.md)的 [[建立並執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)] 區段。

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 程式設計](programming.md)
- [設計工作流程](designing-workflows.md)
- [快速入門教學課程](getting-started-tutorial.md)
- [作法：建立活動](how-to-create-an-activity.md)
- [作法：執行工作流程](how-to-run-a-workflow.md)
