---
title: "Troubleshooting the DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, troubleshooting"
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Troubleshooting the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

本主題列出使用 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項時可能發生的常見問題。  
  
## 不會引發 DataRepeater 鍵盤和滑鼠事件  
 未引發某些 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項事件 \(例如鍵盤和滑鼠事件\)。  這是設計上的預期行為。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項本身是 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 物件的容器，無法在執行階段進行存取。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 在設計階段不會公開 \(Expose\) 事件，  因此當項目獲得焦點 \(Focus\) 時，按下項目或按鍵盤按鍵並不會引發事件。  
  
 不過，如果為 <xref:System.Windows.Forms.Control.Padding%2A> 屬性設定之值的大小足以公開 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的邊緣，則為上述之例外狀況。  在這種狀況下，按下公開的邊界將引發滑鼠事件。  
  
 若要解決這個問題，請將 <xref:System.Windows.Forms.Panel> 控制項加入至 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 區段，再將其他的控制項加入至 <xref:System.Windows.Forms.Panel>。  然後，您就可以將程式碼加入至 <xref:System.Windows.Forms.Panel> 控制項的事件處理常式，處理鍵盤和滑鼠事件。  
  
## DataRepeater 部分隱藏在繫結導覽後面  
 當您先將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項加入至表單，然後再從 \[**資料來源**\] 視窗加入資料繫結控制項時，<xref:System.Windows.Forms.BindingNavigator> 控制項可能會顯示在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的最上層。  此為 \[**資料來源**\] 視窗已知的限制，而且它與其他控制項 \(例如 <xref:System.Windows.Forms.DataGridView> 控制項\) 的行為一致。  
  
 您可以在設計階段將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 移到 <xref:System.Windows.Forms.BindingNavigator> 控制項的下層，或是在 `Load` 事件處理常式中加入與下列類似的程式碼。  
  
```vb#  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```c#  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## 控制項在執行階段沒有正確顯示  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中的某些控制項在執行階段可能無法如預期顯示。  從 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 將控制項複製 \(Clone\) 至 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 時所使用的程序不一定每次都能判斷所有控制項的所有屬性。  例如，如果您在設計階段將未繫結 <xref:System.Windows.Forms.ListBox> 控制項加入至 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項，並以字串清單填入 \(Populate\) 其 <xref:System.Windows.Forms.ListBox.Items%2A> 集合，則 <xref:System.Windows.Forms.ListBox> 在執行階段會是空的。  這是因為複製程序無法將 <xref:System.Windows.Forms.ListBox.Items%2A> 屬性納入考量。  
  
 您可以還原 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> 事件 \(會在預設複製完成後發生\) 中遺失的屬性，藉以修正這類的問題。  下列範例示範如何在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> 事件處理常式中修復 <xref:System.Windows.Forms.ListBox> 控制項的 <xref:System.Windows.Forms.ListBox.Items%2A> 集合。  
  
 [!code-cs[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DataRepeaterItemClonedCS/ItemCloned.cs#1)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/DataRepeaterItemCloned/ItemCloned.vb#1)]  
  
## 遺失項目標題的選取符號  
 在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中變更項目標題的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> 屬性時，某些色彩選擇可能會使選取符號消失。  此外，變更 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 屬性也可能會造成選取符號消失。  
  
 選取符號的色彩及大小是無法變更的。  
  
-   如果將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> 設定為 <xref:System.Drawing.Color.White%2A>，則項目第一次被選取時並不會顯示選取符號。  
  
-   如果將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> 設定為 <xref:System.Drawing.Color.Black%2A>，則選取控制項時並不會顯示選取符號，而且控制項處於編輯模式時也不會顯示鉛筆符號。  
  
-   如果 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 屬性值是設定為小於 11，則在項目標題中不會顯示指示器符號。  
  
 藉由使用 <xref:System.Windows.Forms.PictureBox> 控制項，並在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件中監視 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>，您可以自行提供項目標題和選取符號。  如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>。  
  
## 請參閱  
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)