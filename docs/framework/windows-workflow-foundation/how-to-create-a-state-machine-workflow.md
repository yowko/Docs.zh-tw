---
title: "HOW TO：建立狀態機器工作流程 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# HOW TO：建立狀態機器工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。本主題逐步解說如何建立工作流程，該工作流程會使用 <xref:System.Activities.Statements.StateMachine> 活動等內建活動，以及舊版 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)主題的自訂活動。此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。若要完成此主題，您必須先完成 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation \(WF45\) \- 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### 建立工作流程  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**NumberGuessWorkflowActivities**\]，然後依序選取 \[**加入**\]、\[**新增項目**\]。  
  
2.  在 \[**已安裝**\]、\[**一般項目**\] 節點中，選取 \[**工作流程**\]。選取 \[**工作流程**\] 清單中的 \[**活動**\]。  
  
3.  在 \[**名稱**\] 方塊中，輸入 `StateMachineNumberGuessWorkflow`，並按一下 \[**加入**\]。  
  
4.  從 \[**工具箱**\] 的 \[**狀態機器**\] 區段，將 \[**StateMachine**\] 活動拖放到工作流程設計介面上的 \[**在此放置活動**\] 標籤。  
  
### 若要建立工作流程變數和引數  
  
1.  如果 **StateMachineNumberGuessWorkflow.xaml** 尚未顯示在設計工具中，請在 \[**方案總管**\] 中按兩下該工作流程加以顯示。  
  
2.  按一下工作流程設計工具左下角的 \[**引數**\]，顯示 \[**引數**\] 窗格。  
  
3.  按一下 \[**建立引數**\]。  
  
4.  在 \[**名稱**\] 方塊中輸入 `MaxNumber`，選取 \[**方向**\] 下拉式清單中的 \[**In**\]，選取 \[**引數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存引數。  
  
5.  按一下 \[**建立引數**\]。  
  
6.  在此新加入之 `MaxNumber` 引數下的 \[**名稱**\] 方塊中輸入 `Turns`，選取 \[**方向**\] 下拉式清單中的 \[**Out**\]，選取 \[**引數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER。  
  
7.  按一下活動設計工具左下角的 \[**引數**\]，關閉 \[**引數**\] 窗格。  
  
8.  按一下工作流程設計工具左下角的 \[**變數**\]，顯示 \[**變數**\] 窗格。  
  
9. 按一下 \[**建立變數**\]。  
  
    > [!TIP]
    >  如果沒有顯示 \[**建立變數**\] 方塊，請按一下工作流程設計工具介面上的 <xref:System.Activities.Statements.StateMachine> 活動，選取該活動。  
  
10. 在 \[**名稱**\] 方塊中輸入 `Guess`，選取 \[**變數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存變數。  
  
11. 按一下 \[**建立變數**\]。  
  
12. 在 \[**名稱**\] 方塊中輸入 `Target`，選取 \[**變數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER 儲存變數。  
  
13. 按一下活動設計工具左下角的 \[**變數**\]，關閉 \[**變數**\] 窗格。  
  
### 若要加入工作流程活動  
  
1.  按一下 \[**State1**\] 加以選取。在 \[**屬性視窗**\] 中，將 \[**DisplayName**\] 變更為 `Initialize Target`。  
  
    > [!TIP]
    >  如果沒有顯示 \[**屬性視窗**\]，請從 \[**檢視**\] 功能表選取 \[**屬性視窗**\]。  
  
2.  在工作流程設計工具中按兩下剛剛重新命名的 \[**初始化目標**\] 狀態，將其展開。  
  
3.  將 \[**Assign**\] 活動從 \[**工具箱\]**\] 的 \[**基本**\] 區段拖放到狀態的 \[**項目**\] 區段上。在 \[**到**\] 方塊中輸入 `Target`，然後在 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入下列運算式。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果沒有顯示 \[**工具箱**\] 視窗，請從 \[**檢視**\] 功能表中選取 \[**工具箱**\]。  
  
4.  按一下工作流程設計工具最上方階層連接列中的 \[**StateMachine**\]，返回工作流程設計工具中的整體狀態機器檢視。  
  
5.  將 \[**State** \] 活動從 \[**工具箱**\] 的 \[**狀態機器**\] 區段拖放到工作流程設計工具上，並將它移到 \[**初始化目標**\] 狀態上方。請注意，將新狀態移到 \[**初始化目標**\] 上方時，周圍會出現四個三角形。將新狀態放置在 \[**初始化目標**\] 狀態正下方的三角形上。這樣會將新狀態放置到工作流程上，並且建立從 \[**初始化目標**\] 狀態到新狀態的轉換。  
  
6.  按一下 \[**State1**\] 加以選擇，將 \[**DisplayName**\] 變更為 `Enter Guess`，然後在工作流程設計工具中按兩下該狀態以展開。  
  
7.  將 \[**WriteLine**\] 活動從 \[**工具箱**\] 的 \[**基本**\] 區段拖放到狀態的 \[**項目**\] 區段上。  
  
8.  在 \[**WriteLine** \] 的 \[**Text** \] 屬性方塊中輸入下列運算式。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. 將 \[**Assign**\] 活動從 \[**工具箱**\] 的 \[**基本**\] 區段拖放到狀態的 \[**結束**\] 區段上。  
  
10. 在 \[**到**\] 方塊中輸入 `Turns`，然後在 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入 `Turns + 1`。  
  
11. 按一下工作流程設計工具最上方階層連接列中的 \[**StateMachine**\]，返回工作流程設計工具中的整體狀態機器檢視。  
  
12. 從 \[**工具箱**\] 的 \[**狀態機器**\] 區段，將 \[**FinalState**\] 活動拖放到 \[**輸入猜測**\] 狀態上方，然後將它放置到出現在 \[**輸入猜測**\] 狀態右邊的三角形上，以在 \[**輸入猜測**\] 與 \[**FinalState**\] 之間建立轉換。  
  
13. 轉換的預設名稱是 \[**T2**\]。按一下工作流程設計工具中的轉換加以選取，然後將其 \[**DisplayName**\] 設為「**猜測正確**」。然後按一下並選取 \[**FinalState**\] 並拖放到右側，使其有空間顯示完整的轉換名稱，而不會重疊任何一個狀態。這將可以更容易完成教學課程中的其他步驟。  
  
14. 在工作流程設計工具中按兩下剛剛重新命名的 \[**猜測正確**\] 轉換，將其展開。  
  
15. 從 \[**工具箱**\] 的 \[**NumberGuessWorkflowActivities**\] 區段中，將 \[**ReadInt**\] 活動拖放到轉換的 \[**觸發程序**\] 區段。  
  
16. 在 \[**ReadInt**\] 活動的 \[**屬性視窗**\] 中，將 `"EnterGuess"` \(含引號\) 輸入 \[**BookmarkName**\] 屬性值方塊中，然後在 \[**Result**\] 屬性值方塊中輸入 `Guess`。  
  
17. 在 \[**猜測正確**\] 轉換的 \[**Condition**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. 按一下工作流程設計工具最上方階層連接列中的 \[**StateMachine**\]，返回工作流程設計工具中的整體狀態機器檢視。  
  
    > [!NOTE]
    >  收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。針對此轉換，如果使用者的 `Guess` 符合隨機產生的 `Target`，則會將控制傳遞到 \[**FinalState**\]，同時完成工作流程。  
  
19. 依據猜測是否正確，工作流程應轉換到 \[**FinalState**\] 或回到 \[**輸入猜測**\] 狀態，重新猜測。兩種轉換共用相同的等候觸發程序，等候經由 \[**ReadInt**\] 活動接收使用者的猜測。這稱為共用轉換。若要建立共用轉換，請按一下表示 \[**猜測正確**\] 開始轉換的圓形，然後拖放所需的狀態。本範例中的轉換是自行轉換，因此，請將 \[**猜測正確**\] 轉換的起點拖放到 \[**輸入猜測**\] 狀態的底部。建立轉換後，在工作流程設計工具中選取該轉換，然後將其 \[**DisplayName**\] 屬性設為 \[**猜測不正確**\]。  
  
    > [!NOTE]
    >  共用轉換可以從轉換設計工具內建立，方式是按一下轉換設計工具底部的 \[**新增共用的觸發程序轉換**\]，然後從 \[**要連線的可用狀態**\] 下拉式清單選取想要的目標狀態。  
  
    > [!NOTE]
    >  請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` \(或所有共用觸發轉換的條件皆評估為 `false`\)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。由於設定條件的方式，在本教學課程中不會發生這種情況 \(我們對於猜測是否正確有具體的動作\)。  
  
20. 在工作流程設計工具中按兩下 \[**猜測不正確**\] 轉換，將其展開。請注意，\[**觸發程序**\] 已設為 \[**猜測正確**\] 轉換所使用的同一個 \[**ReadInt**\] 活動。  
  
21. 在 \[**Condition**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. 從 \[**工具箱**\] 的 \[**控制流程**\] 區段，將 \[**If**\] 活動拖放到轉換的 \[**動作**\] 區段。  
  
23. 在 \[**If**\] 活動的 \[**Condition**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb-c#  
    Guess < Target  
    ```  
  
24. 從 \[**工具箱**\] 的 \[**基本**\] 區段拖放兩個 \[**WriteLine**\] 活動，其中一個拖放到 \[**If**\] 活動的 \[**Then**\] 區段，另一個拖放在 \[**Else**\] 區段。  
  
25. 按一下 \[**Then**\] 區段中的 \[**WriteLine**\] 活動加以選取，並在 \[**Text**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb-c#  
    "Your guess is too low."  
    ```  
  
26. 按一下 \[**Else**\] 區段中的 \[**WriteLine**\] 活動加以選取，並在 \[**Text**\] 屬性值方塊中輸入下列運算式。  
  
    ```vb-c#  
    "Your guess is too high."  
    ```  
  
27. 按一下工作流程設計工具最上方階層連接列中的 \[**StateMachine**\]，返回工作流程設計工具中的整體狀態機器檢視。  
  
     下列範例示範完成的工作流程。  
  
     ![已完成的狀態機器工作流程](../../../docs/framework/windows-workflow-foundation//media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### 若要建置工作流程  
  
1.  按下 CTRL\+SHIFT\+B 建置方案。  
  
     如需如何執行工作流程的指示，請參閱下一個主題 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)。如果您已經使用另一個樣式的工作流程完成 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) 步驟，並且想要從這個步驟開始使用狀態機器工作流程執行，請直接跳到 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md) 的[若要建置及執行應用程式](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一節。  
  
## 請參閱  
 <xref:System.Activities.Statements.Flowchart>   
 <xref:System.Activities.Statements.FlowDecision>   
 [Windows Workflow Foundation 程式設計](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [設計工作流程](../../../docs/framework/windows-workflow-foundation//designing-workflows.md)   
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [HOW TO：建立活動](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)   
 [HOW TO：執行工作流程](../../../docs/framework/windows-workflow-foundation//how-to-run-a-workflow.md)