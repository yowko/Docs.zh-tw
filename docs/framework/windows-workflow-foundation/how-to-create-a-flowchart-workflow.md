---
title: HOW TO：建立流程圖工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 0faf4d77b1ea2881ba8e029d544f2e42cf552349
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989680"
---
# <a name="how-to-create-a-flowchart-workflow"></a>作法：建立流程圖工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題將逐步說明如何建立使用內建活動（例如<xref:System.Activities.Statements.Flowchart>活動）的工作流程，以及先前[如何執行的自訂活動：建立活動](how-to-create-an-activity.md)主題。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
> 「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先[完成如何：建立活動](how-to-create-an-activity.md)。  
  
> [!NOTE]
> 若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1. 以滑鼠右鍵按一下**方案總管**中的 **[numberguessworkflowactivities]** ，然後選取 [**加入**]、[**新增專案**]。  
  
2. 在 [**已安裝**的**通用專案**] 節點中，選取 [**工作流程**]。 從 [**工作流程**] 清單中選取 [**活動**]。  
  
3. 在`FlowchartNumberGuessWorkflow` [**名稱**] 方塊中輸入，然後按一下 [**新增**]。  
  
4. 從 [**工具箱**] 的 [**流程圖**] 區段，將 [ **flowchart** ] 活動拖放到工作流程設計介面上的 [在**此放置活動**] 標籤上。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1. 按兩下**方案總管**中的 [ **FlowchartNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。  
  
2. 在工作流程設計工具的左下方按一下 [**引數**]，以顯示 [**引數**] 窗格。  
  
3. 按一下 [**建立引數**]。  
  
4. 在`MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [In]，選取 [自**變數型**別] 下拉式清單**中**的 [ **Int32** ]，然後按下 enter 以儲存引數。  
  
5. 按一下 [**建立引數**]。  
  
6. 在`Turns`新加入的引數下方輸入 [名稱] 方塊，從 [方向] 下拉式清單中選取 [Out]，選取 [引數型別] 下拉式清單中的 [Int32]，然後按 enter。 `MaxNumber`  
  
7. 在活動設計工具的左下方按一下 [**引數**]，以關閉 [**引數**] 窗格。  
  
8. 按一下工作流程設計工具左下方的 [**變數**]，以顯示 [**變數**] 窗格。  
  
9. 按一下 [**建立變數**]。  
  
    > [!TIP]
    > 如果沒有顯示 [**建立變數**] 方塊，請<xref:System.Activities.Statements.Flowchart>按一下工作流程設計工具介面上的活動加以選取。  
  
10. 在`Guess` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
11. 按一下 [**建立變數**]。  
  
12. 在`Target` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
13. 在活動設計工具的左下方按一下 [**變數**]，以關閉 [**變數**] 窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1. 從 [**工具箱**] 的 [**基本**] 區段中拖曳 [**指派**] 活動，並將其暫留在 [**開始**] 節點上（位於流程圖頂端）。 當 [**指派**] 活動超過 [**啟動**] 節點時，[**開始**] 節點周圍會出現三個三角形。 將 [**指派**] 活動放置在 [**開始**] 節點正下方的三角形上。 這會將兩個專案連結在一起，並將 [**指派**] 活動指定為流程圖中的第一個活動。  
  
    > [!NOTE]
    > 您也可以手動連結活動與啟動節點，指定活動為工作流程中的啟動活動。 若要這麼做，請將滑鼠游標移到 [**開始**] 節點上方，按一下滑鼠停留在 [**啟動**] 節點上方時出現的其中一個矩形，然後將連接線向下拖曳到所需的活動，並放置在出現的其中一個矩形上。 您也可以在活動上按一下滑鼠右鍵，然後選擇 [**設定為起始節點**]，將它指定為開始活動。  
  
2. 在`Target` [**到**] 方塊中輸入，並在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入下列運算式。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > 如果沒有顯示 [**工具箱**] 視窗，請從 [**視圖**] 功能表中選取 [**工具箱**]。  
  
3. 從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段拖曳 [**提示**] 活動，將它放在上一個步驟的 [**指派**] 活動下方，然後將 [**提示**] 活動連接至 [**指派**] 活動。 有三種方式可連接這兩個活動。 第一種方式是在您將 [**提示**] 活動放在工作流程上時進行連接。 當您將 [**提示**] 活動拖曳到工作流程時，請將其暫留在 [**指派**] 活動上方，然後放**到 [** **指派**] 活動上方的四個三角形其中之一。 第二種方式是將 [**提示**] 活動放置到所需位置的工作流程上。 然後，將滑鼠停留在 [**指派**] 活動上方，並將出現的其中一個矩形拖曳到 [**提示**] 活動。 拖曳滑鼠，使 [**指派**] 活動中的連接線連接至 [**提示**] 活動的其中一個矩形，然後放開滑鼠按鍵。 第三種方式與第一種方式非常類似，不同之處在于，它不會從 [**工具箱**] 拖曳 [**提示**] 活動，而是從其在工作流程設計介面上的位置拖曳，將其停留在 [**指派**] 活動上方，然後放到其中一個出現的三角形。  
  
4. 在 [**提示**] 活動的 [ `"EnterGuess"` **屬性] 視窗**中，于 [ **BookmarkName**屬性值] 方塊中輸入包含引號。 在`Guess` [**結果**] 屬性值方塊中輸入，然後在 [ **Text** ] 屬性方塊中輸入下列運算式。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > 如果沒有顯示 [**屬性] 視窗**，請從 [**視圖**] 功能表中選取 [**屬性視窗]** 。  
  
5. 從 [**工具箱**] 的 [**基本**] 區段中拖曳 [**指派**] 活動，並使用上一個步驟中所述的其中一個方法進行連接，使其位於 [**提示**] 活動下方。  
  
6. 在`Turns` [**到**] 方塊中`Turns + 1`輸入，然後在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中鍵入。  
  
7. 從 [**工具箱**] 的 [**流程圖**] 區段中拖曳**FlowDecision** ，並將它連接到 [**指派**] 活動下方。 在 [**屬性] 視窗**的 [**條件**] 屬性值方塊中，輸入下列運算式。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. 從 [**工具箱**] 將另一個 [ **FlowDecision** ] 活動拖放到第一個活動下方。 從頂端**FlowDecision**活動上標示**為 False**的矩形拖曳到第二個**FlowDecision**活動頂端的矩形，以連接這兩個活動。  
  
    > [!TIP]
    > 如果您在**FlowDecision**上看不到 [ **True** ] 和 [ **False** ] 標籤，請將滑鼠停留在**FlowDecision**上。  
  
9. 按一下第二個 [ **FlowDecision** ] 活動加以選取。 在 [**屬性] 視窗**的 [**條件**] 屬性值方塊中，輸入下列運算式。  
  
    ```text
    Guess < Target
    ```  
  
10. 從 [**工具箱**] 的 [**基本**] 區段拖放兩個 [ **WriteLine** ] 活動，使其在兩個**FlowDecision**活動的正下方。 將底部**FlowDecision**活動的**真正**動作連線到最左邊的 [ **writeline** ] 活動，並將 [ **False** ] 動作連接至最右邊的 [ **writeline** ] 活動。  
  
11. 按一下最左邊的 [ **WriteLine** ] 活動加以選取，然後在 [**屬性] 視窗**的 [**文字**] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. 將 [ **WriteLine** ] 連接至其上方的 [**提示**] 活動左邊。  
  
13. 按一下最右邊的 [ **WriteLine** ] 活動加以選取，然後在 [**屬性] 視窗**的 [**文字**] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. 將 [ **WriteLine** ] 活動連接至其上方 [**提示**] 活動的右側。  
  
     下列範例示範完成的工作流程。  
  
     ![顯示已完成 Windows Workflow Foundation 流程圖的圖表。](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1. 按下 CTRL+SHIFT+B 以建置方案。  
  
     如需有關如何執行工作流程的指示，請參閱下一個主題[：如何：執行工作流程](how-to-run-a-workflow.md)。 如果您已經完成[如何：使用不同的](how-to-run-a-workflow.md)工作流程樣式執行工作流程步驟，並想要使用此步驟中的流程圖工作流程執行，請直接跳[至](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [如何：執行工作流程](how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 程式設計](programming.md)
- [設計工作流程](designing-workflows.md)
- [快速入門教學課程](getting-started-tutorial.md)
- [如何：建立活動](how-to-create-an-activity.md)
- [如何：執行工作流程](how-to-run-a-workflow.md)
