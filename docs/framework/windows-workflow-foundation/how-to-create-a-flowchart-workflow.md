---
title: "HOW TO：建立流程圖工作流程 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# HOW TO：建立流程圖工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。本主題逐步解說如何建立工作流程，該工作流程會使用 <xref:System.Activities.Statements.Flowchart> 活動等內建活動，以及舊版 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)主題的自訂活動。此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。若要完成此主題，您必須先完成 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation \(WF45\) \- 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### 建立工作流程  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**NumberGuessWorkflowActivities**\]，然後依序選取 \[**加入**\]、\[**新增項目**\]。  
  
2.  在 \[**已安裝**\]、\[**一般項目**\] 節點中，選取 \[**工作流程**\]。選取 \[**工作流程**\] 清單中的 \[**活動**\]。  
  
3.  在 \[**名稱**\] 方塊中，輸入 `FlowchartNumberGuessWorkflow`，並按一下 \[**加入**\]。  
  
4.  從 \[**工具箱**\] 的 \[**Flowchart**\] 區段，將 \[**Flowchart**\] 活動拖放到工作流程設計介面上的 \[**在此放置活動**\] 標籤。  
  
### 若要建立工作流程變數和引數  
  
1.  如果設計工具中尚未顯示工作流程，請按兩下 \[**方案總管**\] 中的 \[**FlowchartNumberGuessWorkflow.xaml**\] 加以顯示。  
  
2.  按一下工作流程設計工具左下角的 \[**引數**\]，顯示 \[**引數**\] 窗格。  
  
3.  按一下 \[**建立引數**\]。  
  
4.  在 \[**名稱**\] 方塊中輸入 `MaxNumber`，選取 \[**方向**\] 下拉式清單中的 \[**In**\]，選取 \[**引數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存引數。  
  
5.  按一下 \[**建立引數**\]。  
  
6.  在此新加入之 `MaxNumber` 引數下的 \[**名稱**\] 方塊中輸入 `Turns`，選取 \[**方向**\] 下拉式清單中的 \[**Out**\]，選取 \[**引數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER。  
  
7.  按一下活動設計工具左下角的 \[**引數**\]，關閉 \[**引數**\] 窗格。  
  
8.  按一下工作流程設計工具左下角的 \[**變數**\]，顯示 \[**變數**\] 窗格。  
  
9. 按一下 \[**建立變數**\]。  
  
    > [!TIP]
    >  如果沒有顯示 \[**建立變數**\] 方塊，請按一下工作流程設計工具介面上的 <xref:System.Activities.Statements.Flowchart> 活動，選取該活動。  
  
10. 在 \[**名稱**\] 方塊中輸入 `Guess`，選取 \[**變數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存變數。  
  
11. 按一下 \[**建立變數**\]。  
  
12. 在 \[**名稱**\] 方塊中輸入 `Target`，選取 \[**變數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存變數。  
  
13. 按一下活動設計工具左下角的 \[**變數**\]，關閉 \[**變數**\] 窗格。  
  
### 若要加入工作流程活動  
  
1.  從 \[**工具箱**\] 的 \[**Primitives**\] 區段拖曳 \[**指派**\] 活動，然後將該活動移到流程圖最上方的 \[**啟動**\] 節點之上。\[**指派**\] 活動在 \[**啟動**\] 節點之上時，\[**啟動**\] 節點周圍會出現三個三角形。將 \[**指派**\] 活動放置在 \[**啟動**\] 節點正上方的三角形上。這樣會將兩個項目連結起來，並且將 \[**指派**\] 活動指派為該流程圖中的第一個活動。  
  
    > [!NOTE]
    >  您也可以手動連結活動與啟動節點，指定活動為工作流程中的啟動活動。若要這麼做，請將滑鼠游標移到 \[**啟動**\] 節點上方，按一下滑鼠位於 \[**啟動**\] 節點上方時出現的矩形，再將連接線向下拖曳到所需的活動，並放置在出現的其中一個矩形上。您還可以將活動指定為啟動活動，方法是以滑鼠右鍵按一下該活動並選擇 \[**設為開始節點**\]。  
  
2.  在 \[**到**\] 方塊中輸入 `Target`，然後在 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入下列運算式。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果沒有顯示 \[**工具箱**\] 視窗，請從 \[**檢視**\] 功能表中選取 \[**工具箱**\]。  
  
3.  從 \[**工具箱**\] 的 \[**NumberGuessWorkflowActivities**\] 區段，將 \[**提示**\] 活動拖放到上一個步驟的 \[**指派**\] 活動下方，然後將 \[**提示**\] 活動連接至 \[**指派**\] 活動。有三種方式可連接這兩個活動。第一種方法是在將 \[**提示**\] 活動拖曳到工作流程上時進行連接。當您將 \[**提示**\] 活動拖曳到工作流程時，請將該活動移到 \[**指派**\] 活動上方，並將其放置在 \[**提示**\] 活動位於 \[**指派**\] 活動上方時出現的四個三角形的其中一個。第二種方式是將 \[**提示**\] 活動放置到所需位置的工作流程。接著，將滑鼠游標移到 \[**指派**\] 活動上方，並將出現的其中一個矩形向下拖曳到 \[**提示**\] 活動。拖曳滑鼠，使 \[**指派**\] 活動的連接線連接至 \[**提示**\] 活動的其中一個三角形，然後放開滑鼠按鈕。第三種方式與第一種方式非常類似，只不過不需從 \[**工具箱**\] 拖曳 \[**提示**\] 活動，而是從該活動在工作流程設計介面上的位置拖曳，然後將該活動移到 \[**指派**\] 活動上方，再放置到所出現的其中一個三角形上。  
  
4.  在 \[**提示**\] 活動的 \[**屬性視窗**\] 中，於 \[**BookmarkName**\] 屬性值方塊輸入 `"EnterGuess"` \(含引號\)。在 \[**結果**\] 屬性值方塊中輸入 `Guess`，然後在 \[**文字**\] 屬性方塊中輸入下列運算式。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  如果沒有顯示 \[**屬性視窗**\]，請從 \[**檢視**\] 功能表選取 \[**屬性視窗**\]。  
  
5.  從 \[**工具箱**\] 的 \[**Primitives**\] 區段拖曳 \[**指派**\]，然後使用上一個步驟中說明的其中一個方法進行連接，使其出現在 \[**提示**\] 活動下方。  
  
6.  在 \[**到**\] 方塊中輸入 \[`Turns`\]，然後在 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入 \[`Turns + 1`\]。  
  
7.  從 \[**工具箱**\] 的 \[**Flowchart**\] 區段拖曳 \[**FlowDecision**\]，並連接到 \[**指派**\] 活動下方。在 \[**屬性視窗**\] 中，將下列運算式輸入到 \[**條件**\] 屬性值方塊中。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  從 \[**工具箱**\] 將另一個 \[**FlowDecision**\] 活動拖放到第一個活動下方。從 \[**FlowDecision**\] 活動上方標示 \[**False**\] 的矩形拖曳到第二個 \[**FlowDecision**\] 活動上方的矩形上，連接兩個活動。  
  
    > [!TIP]
    >  如果 \[**FlowDecision**\] 上沒有顯示 \[**True**\] 和 \[**False**\] 標籤，請將滑鼠游標置於 \[**FlowDecision**\] 上方。  
  
9. 按一下第二個 \[**FlowDecision**\] 活動加以選取。在 \[**屬性視窗**\] 中，將下列運算式輸入到 \[**條件**\] 屬性值方塊中。  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
10. 從 \[**工具箱**\] 的 \[**基本**\] 區段拖曳兩個 \[**WriteLine**\] 活動，使其並置於兩個 \[**FlowDecision**\] 活動之下。將底部 \[**FlowDecision**\] 活動的 \[**True**\] 動作連接至最左邊的 \[**WriteLine**\] 活動，然後將 \[**False**\] 動作連接至最右邊的 \[**WriteLine**\] 活動。  
  
11. 按一下最左邊的 \[**WriteLine**\] 活動加以選取，然後在 \[**屬性視窗**\] 的 \[**文字**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb-c#  
    "Your guess is too low."  
    ```  
  
12. 將 \[**WriteLine**\] 連接至在其上方的 \[**Prompt**\] 活動左邊。  
  
13. 按一下最右邊的 \[**WriteLine**\] 活動加以選取，然後在 \[**屬性視窗**\] 的 \[**文字**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb-c#  
    "Your guess is too high."  
    ```  
  
14. 將 \[**WriteLine**\] 活動連接至其上方的 \[**Prompt**\] 活動的右邊。  
  
     下列範例示範完成的工作流程。  
  
     ![已完成的 Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation//media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### 若要建置工作流程  
  
1.  按下 CTRL\+SHIFT\+B 建置方案。  
  
     如需如何執行工作流程的指示，請參閱下一個主題 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)。如果您已經使用另一個樣式的工作流程完成 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) 步驟，並且想要從這個步驟開始使用流程圖工作流程執行，請直接跳到 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) 的[若要建置及執行應用程式](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一節。  
  
## 請參閱  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Windows Workflow Foundation 程式設計](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [設計工作流程](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)