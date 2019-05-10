---
title: HOW TO：建立流程圖工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 10483c747e0f86816db6f03dd8df17472f31f15c
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063781"
---
# <a name="how-to-create-a-flowchart-workflow"></a>HOW TO：建立流程圖工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題將逐步解說如何建立這類使用內建活動的工作流程<xref:System.Activities.Statements.Flowchart>活動，並從先前的自訂活動[How to:建立活動](how-to-create-an-activity.md)主題。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成[How to:建立活動](how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1. 以滑鼠右鍵按一下**NumberGuessWorkflowActivities**中**方案總管**，然後選取**新增**，**新項目**。  
  
2. 在 **已安裝**，**通用的項目**節點中，選取**工作流程**。 選取 **活動**從**工作流程**清單。  
  
3. 型別`FlowchartNumberGuessWorkflow`成**名稱**方塊，然後按一下**新增**。  
  
4. 拖曳**流程圖**活動，從**流程圖**一節**工具箱**拖曳至**活動拖曳到這裏**上加上標籤工作流程設計介面。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1. 按兩下**FlowchartNumberGuessWorkflow.xaml**中**方案總管 中**時所要顯示工作流程設計工具中，在不顯示。  
  
2. 按一下 **引數**以顯示工作流程設計工具左下角**引數**窗格。  
  
3. 按一下  **Vytvořit Argument**。  
  
4. 型別`MaxNumber`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。  
  
5. 按一下  **Vytvořit Argument**。  
  
6. 型別`Turns`成**名稱**下方新增`MaxNumber`引數，選取**Out**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按 ENTER 鍵。  
  
7. 按一下 **引數**關閉的活動設計工具左下角**引數**窗格。  
  
8. 按一下 **變數**以顯示工作流程設計工具左下角**變數**窗格。  
  
9. 按一下 **建立的變數**。  
  
    > [!TIP]
    >  如果沒有**建立變數**] 方塊中，請按一下 [<xref:System.Activities.Statements.Flowchart>活動在工作流程設計工具介面，以選取它。  
  
10. 型別`Guess`成**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
11. 按一下 **建立的變數**。  
  
12. 型別`Target`成**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
13. 按一下 **變數**關閉的活動設計工具左下角**變數**窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1. 拖曳**指派**活動，從**基本型別**一節**工具箱**並將滑鼠移至**啟動**節點，也就是在頂端流程圖。 當**指派**活動是透過**開始**節點，周圍，就會出現三個三角形**啟動**節點。 卸除**指派**下方的三角形上的活動**開始**節點。 這會連結兩個項目在一起，並指定**指派**為第一個活動，在流程圖中的活動。  
  
    > [!NOTE]
    >  您也可以手動連結活動與啟動節點，指定活動為工作流程中的啟動活動。 若要這樣做，請將滑鼠移**開始**節點中，按一下上方有滑鼠時，會顯示該矩形**開始**節點，然後拖曳連接向所需的活動，並將它放在其中一個出現的矩形。 您也可以指定做為起始的活動的活動，以滑鼠右鍵按一下 it 選擇**設為開始節點**。  
  
2. 型別`Target`成**要** 方塊中，下列運算式**輸入 C# 運算式**或**輸入 VB 運算式** 方塊中。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。  
  
3. 拖曳**提示**活動，從**NumberGuessWorkflowActivities**一節**工具箱**，下方**指派**活動從上一個步驟，並連接**提示**活動**指派**活動。 有三種方式可連接這兩個活動。 第一個方法是將它們連接，當您卸除**提示**在工作流程的活動。 當您拖曳**提示**活動至工作流程，停留**指派**活動拖曳至顯示四個三角形的其中一個**提示**活動是透過**指派**活動。 第二種方式是卸除**提示**到所需位置的工作流程的活動。 然後，將滑鼠移**指派**活動並拖曳其中一個矩形向下至出現**提示**活動。 拖曳滑鼠，使連接線**指派**活動連線至其中一個三角形**提示**活動，然後放開滑鼠按鈕。 第三種方法是非常類似於第一個方法，除了，而不是拖曳**提示**活動，從**工具箱**，您將它從其位置拖曳工作流程設計介面上，停留**指派**活動拖曳至其中一個三角形出現。  
  
4. 在**屬性 視窗**for**提示**活動中，輸入`"EnterGuess"`包括到引號**BookmarkName**屬性值方塊。 型別`Guess`成**結果**屬性值方塊中，並輸入下列運算式**文字**屬性方塊中。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  如果**屬性 視窗**顯示，請選取**屬性視窗**從**檢視**功能表。  
  
5. 拖曳**指派**活動，從**基本型別**一節**工具箱**並將它使用其中一個方法，讓它低於上一個步驟中所述連接**提示**活動。  
  
6. 型別`Turns`成**要**方塊和`Turns + 1`到**輸入 C# 運算式**或**輸入 VB 運算式** 方塊中。  
  
7. 拖曳**FlowDecision**從**流程圖**一節**工具箱**並將它連接下列**指派**活動。 在 [**屬性] 視窗**，輸入下列運算式**條件**屬性值方塊。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. 將另一個**FlowDecision**活動，從**工具箱**並將它放在第一個文字方塊下方。 從標示為矩形拖曳來連接兩個活動**假**頂端**FlowDecision**矩形頂端的第二個活動**FlowDecision**活動。  
  
    > [!TIP]
    >  如果您看不見 **，則為 True**和**False**標籤上**FlowDecision**，停留**FlowDecision**。  
  
9. 按一下第二個**FlowDecision**活動加以選取。 在 [**屬性] 視窗**，輸入下列運算式**條件**屬性值方塊。  
  
    ```
    Guess < Target  
    ```  
  
10. 將兩個**WriteLine**活動，從**基本型別**一節**工具箱**和卸除它們，讓它們並排顯示以下兩個**FlowDecision**活動。 連接 **，則為 True**下方的動作**FlowDecision**至最左邊**WriteLine**活動，而**False**動作最右邊**WriteLine**活動。  
  
11. 按一下最左邊**WriteLine**活動加以選取，然後輸入下列運算式**文字**屬性值方塊中**屬性 視窗**。  
  
    ```
    "Your guess is too low."  
    ```  
  
12. 連接**WriteLine**左側**提示**其上方的活動。  
  
13. 按一下最右邊**WriteLine**活動加以選取，然後輸入下列運算式**文字**屬性值方塊中**屬性 視窗**。  
  
    ```
    "Your guess is too high."  
    ```  
  
14. 連接**WriteLine**活動右側**提示**其上方的活動。  
  
     下列範例示範完成的工作流程。  
  
     ![此圖顯示已完成的 Windows Workflow Foundation 流程圖。](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1. 按下 CTRL+SHIFT+B 以建置方案。  
  
     如需有關如何執行工作流程，指示，請參閱下一個主題中， [How to:執行工作流程](how-to-run-a-workflow.md)。 如果您已經完成[How to:執行工作流程](how-to-run-a-workflow.md)步驟來搭配另一個樣式的工作流程並想要使用此步驟的流程圖工作流程執行，請直接跳到[以建置並執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一節[How to:執行工作流程](how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 程式設計](programming.md)
- [設計工作流程](designing-workflows.md)
- [快速入門教學課程](getting-started-tutorial.md)
- [如何：建立活動](how-to-create-an-activity.md)
- [如何：執行工作流程](how-to-run-a-workflow.md)
