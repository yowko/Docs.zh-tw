---
title: "HOW TO：建立循序工作流程 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# HOW TO：建立循序工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。本主題逐步解說如何建立工作流程，該工作流程會使用 <xref:System.Activities.Statements.Sequence> 活動等內建活動，以及舊版 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)主題的自訂活動。此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。若要完成此主題，您必須先完成 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation \(WF45\) \- 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### 建立工作流程  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**NumberGuessWorkflowActivities**\]，然後依序選取 \[**加入**\]、\[**新增項目**\]。  
  
2.  在 \[**已安裝**\]、\[**一般項目**\] 節點中，選取 \[**工作流程**\]。選取 \[**工作流程**\] 清單中的 \[**活動**\]。  
  
3.  在 \[**名稱**\] 方塊中，輸入 `SequentialNumberGuessWorkflow`，並按一下 \[**加入**\]。  
  
4.  從 \[**工具箱**\] 的 \[**控制流程**\] 區段，將 \[**Sequence**\] 活動拖放到工作流程設計介面上的 \[**在此放置活動**\] 標籤。  
  
### 若要建立工作流程變數和引數  
  
1.  如果設計工具中尚未顯示工作流程，請按兩下 \[**方案總管**\] 中的 **SequentialNumberGuessWorkflow.xaml** 加以顯示。  
  
2.  按一下工作流程設計工具左下角的 \[**引數**\]，顯示 \[**引數**\] 窗格。  
  
3.  按一下 \[**建立引數**\]。  
  
4.  在 \[**名稱**\] 方塊中輸入 `MaxNumber`，選取 \[**方向**\] 下拉式清單中的 \[**In**\]，選取 \[**引數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存引數。  
  
5.  按一下 \[**建立引數**\]。  
  
6.  在此新加入之 `MaxNumber` 引數下的 \[**名稱**\] 方塊中輸入 `Turns`，選取 \[**方向**\] 下拉式清單中的 \[**Out**\]，選取 \[**引數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER。  
  
7.  按一下活動設計工具左下角的 \[**引數**\]，關閉 \[**引數**\] 窗格。  
  
8.  按一下工作流程設計工具左下角的 \[**變數**\]，顯示 \[**變數**\] 窗格。  
  
9. 按一下 \[**建立變數**\]。  
  
    > [!TIP]
    >  如果沒有顯示 \[**建立變數**\] 方塊，請在工作流程設計工具介面上按一下 \[**Sequence**\] 活動加以選取。  
  
10. 在 \[**名稱**\] 方塊中輸入 `Guess`，選取 \[**變數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存變數。  
  
11. 按一下 \[**建立變數**\]。  
  
12. 在 \[**名稱**\] 方塊中輸入 `Target`，選取 \[**變數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存變數。  
  
13. 按一下活動設計工具左下角的 \[**變數**\]，關閉 \[**變數**\] 窗格。  
  
### 若要加入工作流程活動  
  
1.  將 \[**Assign**\] 活動從 \[**工具箱**\] 的 \[**基本**\] 區段拖放到 \[**Sequence**\] 活動上。在 \[**到**\] 方塊中輸入 `Target`，然後在 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入下列運算式。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果沒有顯示 \[**工具箱**\] 視窗，請從 \[**檢視**\] 功能表中選取 \[**工具箱**\]。  
  
2.  在 \[**工具箱**\] 的 \[**控制流程**\] 區段中，將 \[**DoWhile**\] 活動拖放到工作流程上的 \[**Assign**\] 活動下方。  
  
3.  在 \[**DoWhile**\] 活動的 \[**Condition**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <xref:System.Activities.Statements.DoWhile> 活動會執行其子活動，然後評估其 <xref:System.Activities.Statements.DoWhile.Condition%2A>。如果 <xref:System.Activities.Statements.DoWhile.Condition%2A> 判斷值為 `True`，則會再次執行 <xref:System.Activities.Statements.DoWhile> 中的活動。此範例中會評估使用者的猜測，而 <xref:System.Activities.Statements.DoWhile> 會繼續，直到猜測正確為止。  
  
4.  從 \[**工具箱**\] 的 \[**NumberGuessWorkflowActivities**\] 區段，將 \[**Prompt**\] 活動拖放到上一個步驟的 \[**DoWhile**\] 活動下方。  
  
5.  在 \[**屬性視窗**\] 中，於 \[**Prompt**\] 活動的 \[**BookmarkName**\] 屬性值方塊中輸入 `"EnterGuess"` \(含引號\)。在 \[**結果**\] 屬性值方塊中輸入 `Guess`，然後在 \[**文字**\] 屬性方塊中輸入下列運算式。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  如果沒有顯示 \[**屬性視窗**\]，請從 \[**檢視**\] 功能表選取 \[**屬性視窗**\]。  
  
6.  從 \[**工具箱**\] 的 \[**基本**\] 區段中，將 \[**Assign**\] 活動拖放到 \[**DoWhile**\] 活動下方，接在 \[**Prompt**\]活動之後。  
  
    > [!NOTE]
    >  當您卸除 \[**Assign**\] 活動時，請注意工作流程設計工具如何自動加入 \[**Sequence**\] 活動，以同時包含 \[**Prompt**\] 活動和新加入的 \[**Assign**\] 活動。  
  
7.  在 \[**到**\] 方塊中輸入 `Turns`，然後在 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入 `Turns + 1`。  
  
8.  在 \[**工具箱**\] 中，將 \[**控制流程**\] 區段中的 \[**If**\] 活動拖放到 \[**Sequence**\] 活動，接在新加入的 \[**Assign**\] 活動之後。  
  
9. 在 \[**If**\] 活動的 \[**Condition**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. 從 \[**工具箱**\] 的 \[**控制流程**\] 區段，將另一個 \[**If**\] 活動拖放到第一個 \[**If**\] 活動的 \[**Then**\] 區段。  
  
11. 在新加入的 \[**If**\] 活動的 \[**Condition**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
12. 從 \[**工具箱**\] 的 \[**基本**\] 區段拖放兩個 \[**WriteLine**\] 活動，其中一個放置到新加入之 \[**If**\] 活動的 \[**Then**\] 區段，另一個放置在 \[**Else**\] 區段。  
  
13. 按一下 \[**Then**\] 區段中的 \[**WriteLine**\] 活動加以選取，並在 \[**Text**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. 按一下 \[**Else**\] 區段中的 \[**WriteLine**\] 活動加以選取，並在 \[**Text**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     下列範例示範完成的工作流程。  
  
     ![已完成的循序工作流程](../../../docs/framework/windows-workflow-foundation//media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### 若要建置工作流程  
  
1.  按下 CTRL\+SHIFT\+B 建置方案。  
  
     如需如何執行工作流程的指示，請參閱下一個主題 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)。如果您已經使用另一個樣式的工作流程完成 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) 步驟，並且想要從這個步驟開始使用循序工作流程執行，請直接跳到 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) 的[若要建置及執行應用程式](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一節。  
  
## 請參閱  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Windows Workflow Foundation 程式設計](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [設計工作流程](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)