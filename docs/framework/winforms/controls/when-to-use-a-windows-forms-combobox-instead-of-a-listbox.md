---
title: "何時使用 Windows Form ComboBox 取代 ListBox | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繫結控制項, 下拉式方塊"
  - "下拉式方塊, 與清單方塊比較"
  - "ComboBox 控制項 [Windows Form], 與 ListBox 比較"
  - "ListBox 控制項 [Windows Form], 存取項目"
  - "ListBox 控制項 [Windows Form], 加入和移除項目"
  - "ListBox 控制項 [Windows Form], 與 ComboBox 的比較"
  - "ListCount 屬性"
  - "ListIndex 屬性"
  - "Windows Form 控制項, 資料繫結"
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 何時使用 Windows Form ComboBox 取代 ListBox
<xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ListBox> 控制項的行為類似，而且在部分情況下可予以互換。  然而，它們各有適用的時機。  
  
 一般來說，當有建議的選擇清單時，較適用下拉式方塊，而當想要對清單的內容限制輸入時，則較適用清單方塊。  下拉式方塊包含一個文字方塊欄位，因此可輸入不在清單中的選擇。  不過，當 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> 屬性設為 <xref:System.Windows.Forms.ComboBoxStyle> 時，則為例外。  如果發生這種情形，當輸入項目的第一個字母時此控制項就會選取該項目。  
  
 此外，下拉式方塊可節省表單上的空間。  由於完整清單是在使用者按一下向下鍵時才會出現，所以可輕易將下拉式方塊放入無法放入清單方塊的狹小空間。  但是當將 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> 屬性設為 <xref:System.Windows.Forms.ComboBoxStyle> 時則為例外，此時會顯示完整清單，而且下拉式方塊佔用的空間比清單方塊所佔用的空間還大。  
  
## 請參閱  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 [如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)