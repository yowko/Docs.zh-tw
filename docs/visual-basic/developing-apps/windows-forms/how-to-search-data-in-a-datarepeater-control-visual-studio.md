---
title: "How to: Search Data in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, implementing search"
  - "DataRepeater, searching data"
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Search Data in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在使用含有許多資料錄的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項時，您可能想要讓使用者搜尋特定資料錄。  與其搜尋控制項本身的資料，您倒不如可以藉由查詢基礎 <xref:System.Windows.Forms.BindingSource> 來實作搜尋。  如果找到符合項目，就可以使用 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> 屬性選取該項目並將它捲動到檢視。  
  
### 若要實作搜尋  
  
1.  將 <xref:System.Windows.Forms.TextBox> 控制項從 \[**工具箱**\] 拖曳至包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單。  
  
2.  在 \[屬性\] 視窗中，將 \[**Name**\] 屬性變更為 SearchTextBox。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單。  
  
4.  在 \[屬性\] 視窗中，將 \[**Name**\] 屬性變更為 SearchButton。  將 \[**Text**\] 屬性變更為 Search。  
  
5.  按兩下 <xref:System.Windows.Forms.Button> 控制項開啟 \[程式碼編輯器\]，然後將下列程式碼加入至 `SearchButton_Click` 事件處理常式。  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-cs[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     將 *ProductsBindingSource* 取代為您的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 的 <xref:System.Windows.Forms.BindingSource> 名稱，並將 *ProductID* 取代為所要搜尋的欄位名稱。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)