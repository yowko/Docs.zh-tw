---
title: "HOW TO：建立流程圖工作流程"
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
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b7a8eab16b089597eecc03896f86827aae1ad85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a>HOW TO：建立流程圖工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題逐步說明建立使用這兩個內建的活動，例如工作流程<xref:System.Activities.Statements.Flowchart>活動，並從先前的自訂活動[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)主題。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1.  以滑鼠右鍵按一下**NumberGuessWorkflowActivities**中**方案總管 中**選取**新增**，**新項目**。  
  
2.  在**已安裝**，**一般項目**節點中，選取**工作流程**。 選取**活動**從**工作流程**清單。  
  
3.  型別`FlowchartNumberGuessWorkflow`到**名稱**方塊，然後按一下**新增**。  
  
4.  拖曳**流程圖**活動從**流程圖**區段**工具箱**並將其放置**在此置放活動**上加上標籤工作流程設計介面。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1.  按兩下**FlowchartNumberGuessWorkflow.xaml**中**方案總管 中**來顯示工作流程設計工具中，如果未顯示。  
  
2.  按一下**引數**顯示工作流程設計工具的左下方**引數**窗格。  
  
3.  按一下**建立引數**。  
  
4.  型別`MaxNumber`到**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。  
  
5.  按一下**建立引數**。  
  
6.  型別`Turns`到**名稱**下方新增`MaxNumber`引數，選取**出**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER。  
  
7.  按一下**引數**活動設計工具，以關閉的左下方**引數**窗格。  
  
8.  按一下**變數**顯示工作流程設計工具的左下方**變數**窗格。  
  
9. 按一下**建立變數**。  
  
    > [!TIP]
    >  如果沒有**建立變數**顯示方塊中，按一下<xref:System.Activities.Statements.Flowchart>活動在工作流程設計工具介面，即可選取它。  
  
10. 型別`Guess`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
11. 按一下**建立變數**。  
  
12. 型別`Target`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。  
  
13. 按一下**變數**活動設計工具，以關閉的左下方**變數**窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1.  拖曳**指派**活動從**基本型別**區段**工具箱**並將滑鼠停留在**啟動**節點，即在頂端流程圖。 當**指派**活動位於**啟動** 節點，周圍，就會出現三個三角形**啟動**節點。 卸除**指派**活動是正下方的三角形上**啟動**節點。 這會連結兩個項目在一起，並指定**指派**當作流程圖中的第一個活動的活動。  
  
    > [!NOTE]
    >  您也可以手動連結活動與啟動節點，指定活動為工作流程中的啟動活動。 若要這樣做，請將滑鼠游標**啟動**節點中，按一下滑鼠位於上方時出現的矩形**啟動**節點，然後將拖曳連接線向所需的活動並放在其中一個出現的矩形。 您也可以指定做為 it 上按一下滑鼠右鍵，然後選擇開始活動的活動和**設為開始節點**。  
  
2.  型別`Target`到**至** 方塊中，下列運算式**輸入 C# 運算式**或**輸入 VB 運算式**方塊。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。  
  
3.  拖曳**提示**活動從**NumberGuessWorkflowActivities**區段**工具箱**，卸除下列**指派**活動從上一個逐步執行和連接**提示**活動**指派**活動。 有三種方式可連接這兩個活動。 第一種方式是將它們拖曳連接**提示**上工作流程的活動。 當您拖曳**提示**活動至工作流程，停留**指派**活動並放到時出現的四個三角形的其中一個**提示**活動是透過**指派**活動。 第二種方式是將**提示**放置到所需的位置工作流程的活動。 然後，將滑鼠游標**指派**活動並拖曳至出現的矩形**提示**活動。 拖曳滑鼠，讓連接線**指派**活動連接至其中的矩形**提示**活動，然後再放開滑鼠按鈕。 第三個方式是非常類似於第一個方式，不同處在於，而不是拖曳**提示**活動從**工具箱**，您將它從它的位置拖曳工作流程設計介面上，請停留**指派**活動，並放到三角形出現的其中一個。  
  
4.  在**屬性 視窗**如**提示**活動中，輸入`"EnterGuess"`（包含引號） 到**BookmarkName**屬性值方塊。 型別`Guess`到**結果**屬性值方塊中，並輸入下列運算式**文字**屬性方塊中。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  如果**屬性 視窗**顯示，請選取**屬性 視窗**從**檢視**功能表。  
  
5.  拖曳**指派**活動從**基本型別**區段**工具箱**並將它使用其中一個方法在先前步驟中所述，使它低於連接**提示**活動。  
  
6.  型別`Turns`到**至**方塊和`Turns + 1`到**輸入 C# 運算式**或**輸入 VB 運算式**方塊。  
  
7.  拖曳**FlowDecision**從**流程圖**區段**工具箱**並將它連接下列**指派**活動。 在**屬性 視窗**，下列運算式輸入到**條件**屬性值方塊。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  拖曳其他**FlowDecision**活動從**工具箱**下方的第一個。 從標示為矩形拖曳來連接兩個活動**False**在上方**FlowDecision**矩形頂端的第二個活動**FlowDecision**活動。  
  
    > [!TIP]
    >  如果您沒有看到**True**和**False**標籤上**FlowDecision**，將滑鼠游標**FlowDecision**。  
  
9. 按一下第二個**FlowDecision**活動加以選取。 在**屬性 視窗**，下列運算式輸入到**條件**屬性值方塊。  
  
    ```
    Guess < Target  
    ```  
  
10. 拖放兩**WriteLine**活動從**基本型別**區段**工具箱**加以卸除，讓它們並排顯示兩個**FlowDecision**活動。 連接**True**底端的動作**FlowDecision**至最左邊**WriteLine**活動，而**False**動作最右邊**WriteLine**活動。  
  
11. 按一下最左邊**WriteLine**活動加以選取，然後輸入下列運算式**文字**屬性值方塊中**屬性 視窗**。  
  
    ```
    "Your guess is too low."  
    ```  
  
12. 連接**WriteLine**左側**提示**其上方的活動。  
  
13. 按一下最右邊**WriteLine**活動加以選取，然後輸入下列運算式**文字**屬性值方塊中**屬性 視窗**。  
  
    ```
    "Your guess is too high."  
    ```  
  
14. 連接**WriteLine**活動右邊的 list**提示**其上方的活動。  
  
     下列範例示範完成的工作流程。  
  
     ![完成 Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1.  按下 CTRL+SHIFT+B 以建置方案。  
  
     如需有關如何執行工作流程，指示，請參閱下一個主題中，[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。 如果您已經完成[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)步驟與工作流程的不同的樣式和想要執行此程式碼使用流程圖工作流程，此步驟中的，跳到[建置並執行應用程式](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)區段[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Windows Workflow Foundation 程式設計](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [設計工作流程](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [如何：建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [如何：執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
