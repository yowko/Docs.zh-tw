---
title: "HOW TO：建立狀態機器工作流程"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95ba37b123b57ba9f86fefb55a860fb2122ccd3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a>HOW TO：建立狀態機器工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題逐步說明建立使用這兩個內建的活動，例如工作流程<xref:System.Activities.Statements.StateMachine>活動，並從先前的自訂活動[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)主題。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1.  以滑鼠右鍵按一下**NumberGuessWorkflowActivities**中**方案總管 中**選取**新增**，**新項目**。  
  
2.  在**已安裝**，**一般項目**節點中，選取**工作流程**。 選取**活動**從**工作流程**清單。  
  
3.  型別`StateMachineNumberGuessWorkflow`到**名稱**方塊，然後按一下**新增**。  
  
4.  拖曳**StateMachine**活動從**狀態機器**區段**工具箱**並將其放置**在此置放活動**上加上標籤工作流程設計介面中。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1.  按兩下**StateMachineNumberGuessWorkflow.xaml**中**方案總管 中**來顯示工作流程設計工具中，如果未顯示。  
  
2.  按一下**引數**顯示工作流程設計工具的左下方**引數**窗格。  
  
3.  按一下**建立引數**。  
  
4.  型別`MaxNumber`到**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。  
  
5.  按一下**建立引數**。  
  
6.  型別`Turns`到**名稱**下方新增`MaxNumber`引數，選取**出**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER。  
  
7.  按一下**引數**活動設計工具，以關閉的左下方**引數**窗格。  
  
8.  按一下**變數**顯示工作流程設計工具的左下方**變數**窗格。  
  
9. 按一下**建立變數**。  
  
    > [!TIP]
    >  如果沒有**建立變數**顯示方塊中，按一下<xref:System.Activities.Statements.StateMachine>活動在工作流程設計工具介面，即可選取它。  
  
10. 型別`Guess`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
11. 按一下**建立變數**。  
  
12. 型別`Target`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
13. 按一下**變數**活動設計工具，以關閉的左下方**變數**窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1.  按一下**State1**來選取它。 在**屬性 視窗**，變更**DisplayName**至`Initialize Target`。  
  
    > [!TIP]
    >  如果**屬性 視窗**顯示，請選取**屬性 視窗**從**檢視**功能表。  
  
2.  按兩下剛剛重新命名**初始化目標**狀態在工作流程設計工具中將它展開。  
  
3.  拖曳**指派**活動從**基本型別**區段**工具箱**並將其放置**項目**區段的狀態。 型別`Target`到**至** 方塊中，下列運算式**輸入 C# 運算式**或**輸入 VB 運算式**方塊。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。  
  
4.  傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。  
  
5.  拖曳**狀態**活動從**狀態機器**區段**工具箱**拖曳至工作流程設計工具，將滑鼠停留在**初始化目標**狀態。 請注意周圍會出現四個三角形**初始化目標**時的新狀態是透過它的狀態。 [新增] 狀態正下方的三角形上卸除**初始化目標**狀態。 這樣會將新狀態放置到工作流程，並且建立從轉換**初始化目標**狀態為新的狀態。  
  
6.  按一下**State1**加以選擇，變更**DisplayName**至`Enter Guess`，然後按兩下以展開工作流程設計工具中的狀態。  
  
7.  拖曳**WriteLine**活動從**基本型別**區段**工具箱**並將其放置**項目**區段的狀態。  
  
8.  將下列運算式輸入到**文字**屬性方塊**WriteLine**。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. 拖曳**指派**活動從**基本型別**區段**工具箱**拖曳**結束**區段的狀態。  
  
10. 型別`Turns`到**至**方塊和`Turns + 1`到**輸入 C# 運算式**或**輸入 VB 運算式**方塊。  
  
11. 傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。  
  
12. 拖曳**FinalState**活動從**狀態機器**區段**工具箱**，將滑鼠停留在**輸入猜測**狀態，並將它放拖曳至右邊的三角形**輸入猜測**狀態以便之間建立轉換**輸入猜測**和**FinalState**。  
  
13. 轉換的預設名稱是**T2**。 按一下以選取它，並設定工作流程設計工具中的轉換其**DisplayName**至**猜測正確**。 然後按一下並選取**FinalState**，並將它拖曳至右邊，以便挪出空間不重疊的兩個狀態的任何一個顯示完整的轉換名稱。 這將可以更容易完成教學課程中的其他步驟。  
  
14. 按兩下剛剛重新命名**猜測正確**將它展開工作流程設計工具中的轉換。  
  
15. 拖曳**ReadInt**活動從**NumberGuessWorkflowActivities**區段**工具箱**並將它放**觸發程序**區段轉換。  
  
16. 在**屬性 視窗**如**ReadInt**活動中，輸入`"EnterGuess"`（包含引號） 到**BookmarkName**屬性值方塊中，然後`Guess`到**結果**屬性值方塊  
  
17. 將下列運算式輸入到**猜測正確**轉換的**條件**屬性值方塊。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. 傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。  
  
    > [!NOTE]
    >  收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。 針對此轉換，如果使用者的`Guess`符合隨機產生`Target`，則控制權會傳遞給**FinalState**和工作流程完成。  
  
19. 根據先前的猜測是否正確，工作流程應轉換到**FinalState**或返回**輸入猜測**狀態再試一次。 兩種轉換共用相同觸發程序的等待接收透過使用者的猜測**ReadInt**活動。 這稱為共用轉換。 若要建立共用的轉換，請按一下 的圓形，表示開始**猜測正確**轉換，並將它拖曳到所需的狀態。 在此情況下轉換是自行轉換，因此的起點拖放到**猜測正確**轉換拖放回到底部**輸入猜測**狀態。 建立轉換之後, 在工作流程設計工具中選取它，並設定其**DisplayName**屬性**猜測不正確**。  
  
    > [!NOTE]
    >  共用的轉換也會建立從轉換設計工具內按一下**新增共用的觸發程序轉換**底部的轉換設計工具，然後選取 從想要的目標狀態**要連線的可用狀態**下拉式清單。  
  
    > [!NOTE]
    >  請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` (或所有共用觸發轉換的條件皆評估為 `false`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。 由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。  
  
20. 按兩下**猜測不正確**將它展開工作流程設計工具中的轉換。 請注意，**觸發程序**已經設定為相同**ReadInt**所使用的活動**猜測正確**轉換。  
  
21. 將下列運算式輸入到**條件**屬性值方塊。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. 拖曳**如果**活動從**控制流程**區段**工具箱**並將它放**動作**轉換的區段。  
  
23. 將下列運算式輸入到**如果**活動的**條件**屬性值方塊。  
  
    ```
    Guess < Target  
    ```  
  
24. 拖放兩**WriteLine**活動從**基本型別**區段**工具箱**，讓其中一項是置於**然後**區段**如果**活動和一個處於**Else** > 一節。  
  
25. 按一下**WriteLine**中的活動**然後**區段來選取它，然後輸入下列運算式**文字**屬性值方塊。  
  
    ```
    "Your guess is too low."  
    ```  
  
26. 按一下**WriteLine**中的活動**Else**區段來選取它，然後輸入下列運算式**文字**屬性值方塊。  
  
    ```
    "Your guess is too high."  
    ```  
  
27. 傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。  
  
     下列範例示範完成的工作流程。  
  
     ![已完成狀態機器工作流程](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1.  按下 CTRL+SHIFT+B 以建置方案。  
  
     如需有關如何執行工作流程，指示，請參閱下一個主題中，[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。 如果您已經完成[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)步驟來搭配不同的工作流程的樣式和想要執行此程式碼使用狀態機器工作流程，此步驟中的，跳到[建置並執行應用程式](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)區段[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Windows Workflow Foundation 程式設計](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [設計工作流程](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [如何：建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [如何：執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
