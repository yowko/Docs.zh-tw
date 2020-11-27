---
title: 作法：建立流程圖工作流程
description: 本文說明如何建立工作流程，以使用內建活動和前一篇文章中的自訂活動。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: f8e0703591629a72e0a8f6eeb05dd9d19c8c4c91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275823"
---
# <a name="how-to-create-a-flowchart-workflow"></a>作法：建立流程圖工作流程

工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題逐步解說如何建立工作流程，此工作流程會使用活動等內建活動 <xref:System.Activities.Statements.Flowchart> ，以及先前的 how [To：建立活動](how-to-create-an-activity.md) 主題的自訂活動。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
> 「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成 [如何：建立活動](how-to-create-an-activity.md)。  
  
> [!NOTE]
> 若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1. 以滑鼠右鍵按一下 **方案總管** 中的 **[numberguessworkflowactivities]** **，然後選取 [** 新增]、[**新增專案**]。  
  
2. 在 [ **已安裝** 的 **一般專案** ] 節點中，選取 [ **工作流程**]。 從 **[工作流程]** 清單中選取 **[活動]**。  
  
3. `FlowchartNumberGuessWorkflow`在 [**名稱**] 方塊中輸入，然後按一下 [**新增**]。  
  
4. 從 [**工具箱**] 的 [**流程圖**] 區段中，將 [ **flowchart** ] 活動拖放到工作流程設計介面上的 [在 **此放置活動**] 標籤。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1. 按兩下 **方案總管** 中的 [ **FlowchartNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。  
  
2. 在工作流程設計工具的左下方按一下 [ **引數** ]，以顯示 [ **引數** ] 窗格。  
  
3. 按一下 **[建立引數]**。  
  
4. 在 `MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [加入]，從 [**引數類型**] 下拉式清單 **中** 選取 [ **Int32** ]，然後按 enter 儲存引數。  
  
5. 按一下 **[建立引數]**。  
  
6. 在 `Turns` 新加入之引數底下的 [**名稱**] 方塊中輸入 `MaxNumber` ，從 [**方向**] 下拉式清單 **中** 選取 [從自 **變數類型**] 下拉式清單選取 [ **Int32** ]，然後按 enter 鍵。  
  
7. 在活動設計工具的左下方按一下 **[引數]**，以關閉 **[引數]** 窗格。  
  
8. 在工作流程設計工具的左下方按一下 [ **變數** ]，以顯示 [ **變數** ] 窗格。  
  
9. 按一下 **[建立變數]**。  
  
    > [!TIP]
    > 如果未顯示 [ **建立變數** ] 方塊，請按一下 <xref:System.Activities.Statements.Flowchart> 工作流程設計工具介面上的活動加以選取。  
  
10. 在 `Guess` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
11. 按一下 **[建立變數]**。  
  
12. 在 `Target` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
13. 在活動設計工具的左下方按一下 **[變數]**，以關閉 **[變數]** 窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1. 從 [**工具箱**] 的 [**基本**] 區段中拖曳 [**指派**] 活動，並將其停留在流程圖頂端的 [**開始**] 節點上。 當 **Assign** 活動超過 **開始** 節點時， **開始** 節點周圍會出現三個三角形。 將 [ **指派** ] 活動放置在 [ **啟動** ] 節點正下方的三角形上。 這會將兩個專案連結在一起，並將 [ **指派** ] 活動指定為流程圖中的第一個活動。  
  
    > [!NOTE]
    > 您也可以手動連結活動與啟動節點，指定活動為工作流程中的啟動活動。 若要這樣做，請將滑鼠停留在 [ **開始** ] 節點上方，按一下滑鼠位於 [ **啟動** ] 節點上方時出現的其中一個矩形，再將連接線向下拖曳到所需的活動，然後放在出現的其中一個矩形上。 您也可以用滑鼠右鍵按一下活動，然後選擇 [ **設定為開始節點**]，將活動指定為啟動活動。  
  
2. 在 `Target` [ **到** ] 方塊中輸入，並在 [ **輸入 c # 運算式** ] 或 [ **輸入 VB 運算式** ] 方塊中輸入下列運算式。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > 若 **[工具箱]** 視窗並未顯示，請從 **[檢視]** 功能表中選取 **[工具箱]**。  
  
3. 從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段拖曳 [**提示**] 活動，將它放在上一個步驟的 [**指派**] 活動下方，然後將 [**提示**] 活動連接至 [**指派**] 活動。 有三種方式可連接這兩個活動。 第一種方式是在工作流程上放置 [ **提示** ] 活動時進行連接。 當您將 [ **提示** ] 活動拖曳至工作流程時，請將它移到 [ **指派** ] 活動上方，並放在 [ **提示** ] 活動在 [ **指派** ] 活動上方時出現的四個三角形的其中一個。 第二種方式是將 [ **提示** ] 活動拖放到工作流程中所需的位置。 然後，將滑鼠停留在 [ **指派** ] 活動上方，並將出現的其中一個矩形拖曳至 [ **提示** ] 活動。 拖曳滑鼠，使 [ **指派** ] 活動的連接線連接至 [ **提示** ] 活動的其中一個矩形，然後放開滑鼠按鍵。 第三種方式與第一種方式非常類似，不同之處在于它不會從 [**工具箱**] 拖曳 [**提示**] 活動，而是從其在工作流程設計介面上的位置拖曳，將它移到 [**指派**] 活動上方，並放在出現的其中一個三角形上。  
  
4. 在 [**提示**] 活動的 [**屬性] 視窗** 中，于 `"EnterGuess"` [ **BookmarkName** ] 屬性值方塊中輸入包含引號。 `Guess`在 [**結果**] 屬性值方塊中輸入，並在 [ **Text** ] 屬性方塊中輸入下列運算式。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > 如果未顯示 [**屬性] 視窗**，請從 [ **View** ] 功能表選取 [**屬性視窗]** 。  
  
5. 從 [**工具箱**] 的 [**基本**] 區段中拖曳 [**指派**] 活動，並使用上一個步驟中所述的其中一個方法來連接它，使其位於 [**提示**] 活動下方。  
  
6. 在 [到] 方塊中輸入 `Turns` ，然後 **To** `Turns + 1` 在 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入。  
  
7. 從 [**工具箱**] 的 [**流程圖**] 區段中拖曳 **FlowDecision** ，然後將它連接至 [**指派**] 活動下方。 在 [ **屬性] 視窗** 中，于 [ **條件** ] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. 從 [**工具箱**] 將另一個 **FlowDecision** 活動拖曳至第一個活動下方。 從 **FlowDecision** 活動頂端標示為 **False** 的矩形拖曳至第二個 **FlowDecision** 活動頂端的矩形，以連接這兩個活動。  
  
    > [!TIP]
    > 如果您在 **FlowDecision** 上沒有看到 **True** 和 **False** 標籤，請將滑鼠停留在 **FlowDecision** 上方。  
  
9. 按一下第二個 **FlowDecision** 活動加以選取。 在 [ **屬性] 視窗** 中，于 [ **條件** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    Guess < Target
    ```  
  
10. 從 [**工具箱**] 的 [**基本**] 區段拖放兩個 [ **WriteLine** ] 活動，使其在兩個 **FlowDecision** 活動底下並存。 將底部 **FlowDecision** 活動的 **真正** 動作連線到最左邊的 [ **writeline** ] 活動，並將 [ **False** ] 動作連接至最右邊的 [ **writeline** ] 活動。  
  
11. 按一下最左邊的 [ **WriteLine** ] 活動加以選取，然後在 [**屬性] 視窗** 的 [ **Text** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. 將 **WriteLine** 連接到上面的 [ **提示** ] 活動左側。  
  
13. 按一下最右邊的 [ **WriteLine** ] 活動加以選取，然後在 [**屬性] 視窗** 的 [ **Text** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. 將 [ **WriteLine** ] 活動連接至其上方的 [ **提示** ] 活動右邊。  
  
     下列範例示範完成的工作流程。  
  
     ![顯示已完成之 Windows Workflow Foundation 流程圖的圖表。](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1. 按 CTRL+SHIFT+B 建置解決方案。  
  
     如需如何執行工作流程的指示，請參閱下一個主題 [：如何：執行工作流程](how-to-run-a-workflow.md)。 如果您已經完成 how to：使用不同的工作流程樣式來[執行工作流程](how-to-run-a-workflow.md)步驟，而且想要使用此步驟中的流程圖工作流程來執行它，請直接跳至 how [To：執行工作流程](how-to-run-a-workflow.md)的 [[建立並執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)] 區段。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 程式設計](programming.md)
- [設計工作流程](designing-workflows.md)
- [快速入門教學課程](getting-started-tutorial.md)
- [作法：建立活動](how-to-create-an-activity.md)
- [作法：執行工作流程](how-to-run-a-workflow.md)
