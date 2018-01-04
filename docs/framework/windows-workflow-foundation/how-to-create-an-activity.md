---
title: "HOW TO：建立活動"
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
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a3b9698d6a060120addff52e6600916a2de19fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-activity"></a>HOW TO：建立活動
活動是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的行為核心單位。 活動的執行邏輯可以實作在 Managed 程式碼中，或是使用其他活動來實作。 本主題示範如何建立兩個活動。 第一個活動是簡單的活動，使用程式碼來實作其執行邏輯。 第二個活動的實作則是使用其他活動來定義。 教學課程中的下列步驟將會使用這些活動。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-activity-library-project"></a>建立活動程式庫專案  
  
1.  開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選擇**新增**，**專案**從**檔案**功能表。  
  
2.  展開**其他專案類型**節點**已安裝**，**範本**清單並選取**Visual Studio 方案**。  
  
3.  選取**空白方案**從**Visual Studio 方案**清單。 確認已選取 [.NET Framework 版本] 下拉式清單中的 [ **.NET Framework 4.5** ]。 型別`WF45GettingStartedTutorial`中**名稱**方塊，然後按一下**確定**。  
  
4.  以滑鼠右鍵按一下**WF45GettingStartedTutorial**中**方案總管 中**選擇**新增**，**新專案**。  
  
    > [!TIP]
    >  如果沒有顯示 [ **方案總管** ] 視窗，請選取 [ **檢視** ] 功能表上的 [ **方案總管** ]。  
  
5.  在 [ **已安裝** ] 節點中，選取 [ **Visual C#**]、[ **工作流程** ] (或 [ **Visual Basic**]、[ **工作流程**])。 請確認**.NET Framework 4.5**中選取[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]版本 下拉式清單中。 選取**活動程式庫**從**工作流程**清單。 型別`NumberGuessWorkflowActivities`中**名稱**方塊，然後按一下**確定**。  
  
    > [!NOTE]
    >  依據哪個程式語言設定為主要語言[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]、 **Visual C#**或**Visual Basic**節點可能會顯示在**其他語言**節點**已安裝**節點。  
  
6.  以滑鼠右鍵按一下**Activity1.xaml**中**方案總管 中**選擇**刪除**。 按一下 [ **確定** ] 以確認。  
  
### <a name="to-create-the-readint-activity"></a>若要建立 ReadInt 活動  
  
1.  選擇**加入新項目**從**專案**功能表。  
  
2.  在**已安裝**，**一般項目**節點中，選取**工作流程**。 選取**程式碼活動**從**工作流程**清單。  
  
3.  型別`ReadInt`到**名稱**方塊，然後按一下**新增**。  
  
4.  以下列定義取代現有的 `ReadInt` 定義。  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` 活動衍生自 <xref:System.Activities.NativeActivity%601>，而不是程式碼活動範本預設的 <xref:System.Activities.CodeActivity>。 如果活動提供單一結果 (透過 <xref:System.Activities.CodeActivity%601> 引數公開)，則可使用 <xref:System.Activities.Activity%601.Result%2A>，但 <xref:System.Activities.CodeActivity%601> 不支援使用書籤，因而會使用 <xref:System.Activities.NativeActivity%601>。  
  
### <a name="to-create-the-prompt-activity"></a>若要建立提示活動  
  
1.  按 CTRL+SHIFT+B 以建置專案。 建置專案可將此專案中的 `ReadInt` 活動用來建置此步驟中的自訂活動。  
  
2.  選擇**加入新項目**從**專案**功能表。  
  
3.  在**已安裝**，**一般項目**節點中，選取**工作流程**。 選取**活動**從**工作流程**清單。  
  
4.  型別`Prompt`到**名稱**方塊，然後按一下**新增**。  
  
5.  按兩下**Prompt.xaml**中**方案總管 中**顯示在設計工具中，如果未顯示。  
  
6.  按一下**引數**活動設計工具顯示的左下方**引數**窗格。  
  
7.  按一下**建立引數**。  
  
8.  型別`BookmarkName`到**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。  
  
9. 按一下**建立引數**。  
  
10. 型別`Result`到**名稱**下方新加入的方塊`BookmarkName`引數，選取**出**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER。  
  
11. 按一下**建立引數**。  
  
12. 型別`Text`到**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。  
  
     這三個引數會繫結至下列步驟中加入至 <xref:System.Activities.Statements.WriteLine> 活動之 `ReadInt` 和 `Prompt` 活動的對應引數。  
  
13. 按一下**引數**活動設計工具，以關閉的左下方**引數**窗格。  
  
14. 拖曳**順序**活動從**控制流程**區段**工具箱**並將其放置**在此置放活動**的標籤**提示**活動設計工具。  
  
    > [!TIP]
    >  如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。  
  
15. 拖曳**WriteLine**活動從**基本型別**區段**工具箱**並將其放置**在此置放活動**的標籤**順序**活動。  
  
16. 繫結**文字**引數的**WriteLine**活動**文字**引數的**提示**活動輸入`Text`到**輸入 C# 運算式**或**輸入 VB 運算式**方塊中**屬性**視窗中，然後再按 TAB 鍵兩次。 這樣會將選項移出屬性外，以關閉 IntelliSense 清單成員視窗並儲存屬性值。 這個屬性也可以設定輸入`Text`到**輸入 C# 運算式**或**輸入 VB 運算式**在活動本身的方塊。  
  
    > [!TIP]
    >  如果**屬性 視窗**顯示，請選取**屬性 視窗**從**檢視**功能表。  
  
17. 拖曳**ReadInt**活動從**NumberGuessWorkflowActivities**區段**工具箱**並將它放**順序**活動，接**WriteLine**活動。  
  
18. 繫結**BookmarkName**引數的**ReadInt**活動**BookmarkName**引數的**提示**輸入活動`BookmarkName`到**輸入 VB 運算式**方塊右邊的**BookmarkName**引數中的**屬性 視窗**，然後按下 TAB 鍵兩個時間關閉 IntelliSense 清單成員視窗並儲存屬性。  
  
19. 繫結**結果**引數的**ReadInt**活動**結果**引數的**提示**活動輸入`Result`到**輸入 VB 運算式**方塊右邊的**結果**引數中的**屬性 視窗**，然後按兩次 TAB 鍵。  
  
20. 按下 CTRL+SHIFT+B 以建置方案。  
  
     如需如何使用這些活動，來建立工作流程的指示，請參閱下一個步驟教學課程中， [How to： 建立工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [設計及實作自訂活動](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [如何：建立工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [在自訂活動設計工具中使用 ExpressionTextBox](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
