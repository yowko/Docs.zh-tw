---
title: HOW TO：建立狀態機器工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 654621ab7dd74c26a7fddbd985559a713c0e9df3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773512"
---
# <a name="how-to-create-a-state-machine-workflow"></a>HOW TO：建立狀態機器工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題將逐步解說如何建立這類使用內建活動的工作流程<xref:System.Activities.Statements.StateMachine>活動，並從先前的自訂活動[How to:建立活動](how-to-create-an-activity.md)主題。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成[How to:建立活動](how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1. 以滑鼠右鍵按一下**NumberGuessWorkflowActivities**中**方案總管**，然後選取**新增**，**新項目**。  
  
2. 在 **已安裝**，**通用的項目**節點中，選取**工作流程**。 選取 **活動**從**工作流程**清單。  
  
3. 型別`StateMachineNumberGuessWorkflow`成**名稱**方塊，然後按一下**新增**。  
  
4. 拖曳**StateMachine**活動，從**狀態機器**一節**工具箱**拖曳至**活動拖曳到這裏**上加上標籤工作流程設計介面中。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1. 按兩下**StateMachineNumberGuessWorkflow.xaml**中**方案總管 中**時所要顯示工作流程設計工具中，在不顯示。  
  
2. 按一下 **引數**以顯示工作流程設計工具左下角**引數**窗格。  
  
3. 按一下  **Vytvořit Argument**。  
  
4. 型別`MaxNumber`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。  
  
5. 按一下  **Vytvořit Argument**。  
  
6. 型別`Turns`成**名稱**下方新增`MaxNumber`引數，選取**Out**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按 ENTER 鍵。  
  
7. 按一下 **引數**關閉的活動設計工具左下角**引數**窗格。  
  
8. 按一下 **變數**以顯示工作流程設計工具左下角**變數**窗格。  
  
9. 按一下 **建立的變數**。  
  
    > [!TIP]
    >  如果沒有**建立變數**] 方塊中，請按一下 [<xref:System.Activities.Statements.StateMachine>活動在工作流程設計工具介面，以選取它。  
  
10. 型別`Guess`成**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
11. 按一下 **建立的變數**。  
  
12. 型別`Target`成**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
13. 按一下 **變數**關閉的活動設計工具左下角**變數**窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1. 按一下  **State1**來選取它。 在 [**屬性] 視窗**，變更**DisplayName**到`Initialize Target`。  
  
    > [!TIP]
    >  如果**屬性 視窗**顯示，請選取**屬性視窗**從**檢視**功能表。  
  
2. 按兩下剛剛重新命名**初始化目標**狀態中的工作流程設計工具，將它展開。  
  
3. 拖曳**指派**活動，從**基本型別**一節**工具箱**拖曳至**項目**狀態一節。 型別`Target`成**要** 方塊中，下列運算式**輸入 C# 運算式**或**輸入 VB 運算式** 方塊中。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。  
  
4. 傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。  
  
5. 拖曳**狀態**活動，從**狀態機器**一節**工具箱**拖曳至工作流程設計工具，將滑鼠移至**初始化目標**狀態。 請注意周圍會出現四個三角形**初始化目標**上方有新的狀態時的狀態。 新狀態放置在正下方的三角形**初始化目標**狀態。 這會將新的狀態，到工作流程，並建立從轉換**初始化目標**狀態到新的狀態。  
  
6. 按一下  **State1**來選取它，變更**DisplayName**到`Enter Guess`，然後按兩下以展開工作流程設計工具中的狀態。  
  
7. 拖曳**WriteLine**活動，從**基本型別**一節**工具箱**拖曳至**項目**狀態一節。  
  
8. 輸入下列運算式**文字** 屬性方塊**WriteLine**。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. 拖曳**指派**活動，從**基本型別**一節**工具箱**並放入**結束**狀態一節。  
  
10. 型別`Turns`成**要**方塊和`Turns + 1`到**輸入 C# 運算式**或**輸入 VB 運算式** 方塊中。  
  
11. 傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。  
  
12. 拖曳**FinalState**活動，從**狀態機器**一節**工具箱**，將滑鼠移至**Enter Guess**狀態，並將它放拖曳至右邊的三角形**輸入猜測**狀態，讓之間建立轉換**Enter Guess**並**FinalState**。  
  
13. 轉換的預設名稱是**T2**。 按一下以選取它，並設定工作流程設計工具中的轉換其**DisplayName**要**猜測正確**。 然後按一下並選取**FinalState**，並將它拖曳到右邊，使其沒有完整的轉換名稱，而不會重疊的兩個狀態的其中一個要顯示的空間。 這將可以更容易完成教學課程中的其他步驟。  
  
14. 按兩下剛剛重新命名**猜測正確**中工作流程設計工具，將其展開的轉換。  
  
15. 拖曳**ReadInt**活動，從**NumberGuessWorkflowActivities**一節**工具箱**並將它放**觸發程序**區段轉換。  
  
16. 在 [**屬性] 視窗**的**ReadInt**活動中，輸入`"EnterGuess"`包括到引號**BookmarkName**屬性值方塊，然後輸入`Guess`成**結果**屬性值方塊  
  
17. 輸入下列運算式**猜測正確**轉換**條件**屬性值方塊。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. 傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。  
  
    > [!NOTE]
    >  收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。 針對此轉換，如果使用者的`Guess`符合隨機產生`Target`，則控制權會傳遞給**FinalState**和工作流程完成。  
  
19. 根據先前的猜測是否正確，工作流程應轉換到**FinalState**或回到**輸入猜測**狀態，再試一次。 兩種轉換共用相同觸發程序等待接收透過使用者的猜測**ReadInt**活動。 這稱為共用轉換。 若要建立共用的轉換，請按一下 的圓形，表示開始**猜測正確**轉換，並將它拖曳至所需的狀態。 在此情況下轉換是自行轉換，因此將拖曳的起點**猜測正確**轉換拖放回到底部**Enter Guess**狀態。 建立轉換之後, 在工作流程設計工具中選取它，並設定其**DisplayName**屬性設**猜測不正確**。  
  
    > [!NOTE]
    >  共用的轉換也可以建立從轉換設計工具內依序按一下**新增共用的觸發程序轉換**底部的轉換設計工具，然後選取 所需的目標狀態從**可用的狀態，來連接**下拉式清單。  
  
    > [!NOTE]
    >  請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` (或所有共用觸發轉換的條件皆評估為 `false`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。 由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。  
  
20. 按兩下**猜測不正確**中工作流程設計工具，將其展開的轉換。 請注意，**觸發程序**已設為相同**ReadInt**所使用的活動**猜測正確**轉換。  
  
21. 輸入下列運算式**條件**屬性值方塊。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. 拖曳**如果**活動，從**控制流程**一節**工具箱**並將它放**動作**轉換的區段。  
  
23. 輸入下列運算式**如果**活動的**條件**屬性值方塊。  
  
    ```
    Guess < Target  
    ```  
  
24. 將兩個**WriteLine**活動，從**基本型別**一節**工具箱**和卸除它們，因此，另一個**然後**區段**如果**活動，另一個處於**Else**一節。  
  
25. 按一下  **WriteLine**中的活動**然後**區段以選取它，然後輸入下列運算式**文字**屬性值方塊。  
  
    ```
    "Your guess is too low."  
    ```  
  
26. 按一下  **WriteLine**中的活動**Else**區段以選取它，然後輸入下列運算式**文字**屬性值方塊。  
  
    ```
    "Your guess is too high."  
    ```  
  
27. 傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。  
  
     下列範例示範完成的工作流程。  
  
     ![已完成狀態機器工作流程](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1. 按下 CTRL+SHIFT+B 以建置方案。  
  
     如需有關如何執行工作流程，指示，請參閱下一個主題中， [How to:執行工作流程](how-to-run-a-workflow.md)。 如果您已經完成[How to:執行工作流程](how-to-run-a-workflow.md)步驟來搭配另一個樣式的工作流程並想要使用此步驟的狀態機器工作流程執行，請直接跳到[以建置並執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一節[How to:執行工作流程](how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 程式設計](programming.md)
- [設計工作流程](designing-workflows.md)
- [快速入門教學課程](getting-started-tutorial.md)
- [如何：建立活動](how-to-create-an-activity.md)
- [如何：執行工作流程](how-to-run-a-workflow.md)
