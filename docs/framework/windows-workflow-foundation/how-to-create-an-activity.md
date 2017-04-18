---
title: "HOW TO：建立活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: 39
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 39
---
# HOW TO：建立活動
活動是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的行為核心單位。活動的執行邏輯可以實作在 Managed 程式碼中，或是使用其他活動來實作。本主題示範如何建立兩個活動。第一個活動是簡單的活動，使用程式碼來實作其執行邏輯。第二個活動的實作則是使用其他活動來定義。教學課程中的下列步驟將會使用這些活動。  
  
> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation \(WF45\) \- 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### 建立活動程式庫專案  
  
1.  開啟 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，並依序選取 \[**檔案**\] 功能表中的 \[**新增**\]、\[**專案**\]。  
  
2.  在 \[**已安裝**\]、\[**範本**\] 清單中，展開 \[**其他專案類型**\] 節點，並選取 \[**Visual Studio 方案**\]。  
  
3.  選取 \[**Visual Studio 方案**\] 清單中的 \[**空白方案**\]。確認已選取 \[.NET Framework 版本\] 下拉式清單中的 \[**.NET Framework 4.5**\]。在 \[**名稱**\] 方塊中輸入 `WF45GettingStartedTutorial`，然後按一下 \[**確定**\]。  
  
4.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**WF45GettingStartedTutorial**\]，並選擇 \[**加入**\]、\[**新增專案**\]。  
  
    > [!TIP]
    >  如果沒有顯示 \[**方案總管**\] 視窗，請選取 \[**檢視**\] 功能表上的 \[**方案總管**\]。  
  
5.  在 \[**已安裝**\] 節點中，選取 \[**Visual C\#**\]、\[**工作流程**\] \(或 \[**Visual Basic**\]、\[**工作流程**\]\)。確認已選取 \[[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本\] 下拉式清單中的 \[**.NET Framework 4.5**\]。選取 \[**工作流程**\] 清單中的 \[**活動程式庫**\]。在 \[**名稱**\] 方塊中輸入 `NumberGuessWorkflowActivities`，然後按一下 \[**確定**\]。  
  
    > [!NOTE]
    >  依據設定哪個程式語言為 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主要語言而異，\[**Visual C\#**\] 或 \[**Visual Basic**\] 節點可能會顯示在 \[**已安裝**\] 節點中的 \[**其他語言**\] 節點下。  
  
6.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**Activity1.xaml**\]，再選擇 \[**刪除**\]。按一下 \[**確定**\] 以確認。  
  
### 若要建立 ReadInt 活動  
  
1.  選擇 \[**專案**\] 功能表中的 \[**加入新項目**\]。  
  
2.  在 \[**已安裝**\]、\[**一般項目**\] 節點中，選取 \[**工作流程**\]。選取 \[**工作流程**\] 清單中的 \[**程式碼活動**\]。  
  
3.  在 \[**名稱**\] 方塊中，輸入 `ReadInt`，然後按一下 \[**加入**\]。  
  
4.  以下列定義取代現有的 `ReadInt` 定義。  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` 活動衍生自 <xref:System.Activities.NativeActivity%601>，而不是程式碼活動範本預設的 <xref:System.Activities.CodeActivity>。如果活動提供單一結果 \(透過 <xref:System.Activities.Activity%601.Result%2A> 引數公開\)，則可使用 <xref:System.Activities.CodeActivity%601>，但 <xref:System.Activities.CodeActivity%601> 不支援使用書籤，因而會使用 <xref:System.Activities.NativeActivity%601>。  
  
### 若要建立提示活動  
  
1.  按 CTRL\+SHIFT\+B 以建置專案。建置專案可將此專案中的 `ReadInt` 活動用來建置此步驟中的自訂活動。  
  
2.  選擇 \[**專案**\] 功能表中的 \[**加入新項目**\]。  
  
3.  在 \[**已安裝**\]、\[**一般項目**\] 節點中，選取 \[**工作流程**\]。選取 \[**工作流程**\] 清單中的 \[**活動**\]。  
  
4.  在 \[**名稱**\] 方塊中，輸入 `Prompt`，然後按一下 \[**加入**\]。  
  
5.  如果未顯示的話，請按兩下 \[**方案總管**\] 中的 \[**Prompt.xaml**\]，在設計工具中顯示它。  
  
6.  按一下活動設計工具左下角的 \[**引數**\]，顯示 \[**引數**\] 窗格。  
  
7.  按一下 \[**建立引數**\]。  
  
8.  在 \[**名稱**\] 方塊中輸入 `BookmarkName`，選取 \[**方向**\] 下拉式清單中的 \[**內**\]，再從 \[**引數型別**\] 下拉式清單中選取 \[**字串**\]，然後按 ENTER 儲存引數。  
  
9. 按一下 \[**建立引數**\]。  
  
10. 在新加入之 `BookmarkName` 引數下方的 \[**名稱**\] 方塊中輸入 `Result`，並選取 \[**方向**\] 下拉式清單中的 \[**外**\]，再選取 \[**引數型別**\] 下拉式清單中的 \[**Int32**\]，然後按下 ENTER。  
  
11. 按一下 \[**建立引數**\]。  
  
12. 在 \[**名稱**\] 方塊中輸入 `Text`，並選取 \[**方向**\] 下拉式清單中的 \[**內**\]，再選取 \[**引數型別**\] 下拉式清單中的 \[**字串**\]，然後按下 ENTER 儲存引數。  
  
     這三個引數會繫結至下列步驟中加入至 `Prompt` 活動之 <xref:System.Activities.Statements.WriteLine> 和 `ReadInt` 活動的對應引數。  
  
13. 按一下活動設計工具左下角的 \[**引數**\]，關閉 \[**引數**\] 窗格。  
  
14. 從 \[**工具箱**\] 的 \[**控制流程**\] 區段，將 \[**Sequence**\] 活動拖放到 \[**提示**\] 活動設計工具的 \[**在此放置活動**\] 標籤上。  
  
    > [!TIP]
    >  如果沒有顯示 \[**工具箱**\] 視窗，請從 \[**檢視**\] 功能表中選取 \[**工具箱**\]。  
  
15. 從 \[**工具箱**\] 的 \[**基本**\] 區段，將 \[**WriteLine**\] 活動拖放到 \[**Sequence**\] 活動的 \[**在此放置活動**\] 標籤上。  
  
16. 在 \[**屬性**\] 視窗中的 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入 `Text`，以將 \[**WriteLine**\] 活動的 \[**文字**\] 引數繫結到 \[**Prompt**\] 活動的 \[**文字**\] 引數，然後按兩次 TAB 鍵。這樣會將選項移出屬性外，以關閉 IntelliSense 清單成員視窗並儲存屬性值。您也可以在活動本身的 \[**輸入 C\# 運算式**\] 或 \[**輸入 VB 運算式**\] 方塊中輸入 `Text`，以設定這個屬性。  
  
    > [!TIP]
    >  如果沒有顯示 \[**屬性視窗**\]，請從 \[**檢視**\] 功能表選取 \[**屬性視窗**\]。  
  
17. 從 \[**工具箱**\] 的 \[**NumberGuessWorkflowActivities**\] 區段，將 \[**ReadInt**\] 活動拖放到 \[**Sequence**\] 活動內，使其追蹤 \[**WriteLine**\] 活動。  
  
18. 在 \[**屬性視窗**\] 中 \[**BookmarkName**\] 引數右側的 \[**輸入 VB 運算式**\] 方塊中輸入 `BookmarkName`，將 \[**ReadInt**\] 活動的 \[**BookmarkName**\] 引數繫結至 \[**提示**\] 活動的 \[**BookmarkName**\] 引數，然後按兩次 TAB 鍵關閉 \[IntelliSense\] 清單成員視窗，並儲存屬性。  
  
19. 在 \[**屬性視窗**\] 中 \[**Result**\] 引數右側的 \[**輸入 VB 運算式**\] 方塊中輸入 `Result`，將 \[**ReadInt**\] 活動的 \[**Result**\] 引數繫結至 \[**提示**\] 活動的 \[**Result**\] 引數，然後按兩次 TAB 鍵。  
  
20. 按下 CTRL\+SHIFT\+B 建置方案。  
  
     如需如何使用這些活動來建立工作流程的詳細資訊，請參閱教學課程中的下一步 [HOW TO：建立工作流程](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)。  
  
## 請參閱  
 <xref:System.Activities.CodeActivity>   
 <xref:System.Activities.NativeActivity%601>   
 [設計和實作自訂活動](../../../docs/framework/windows-workflow-foundation//designing-and-implementing-custom-activities.md)   
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [HOW TO：建立工作流程](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)   
 [使用自訂活動設計工具中的 ExpressionTextBox](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)