---
title: "ComboBox 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComboBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "下拉式方塊, 關於下拉式方塊"
  - "ComboBox 控制項 [Windows Form], 關於 ComboBox 控制項"
  - "下拉式清單, ComboBox 控制項"
  - "下拉式清單, Windows Form"
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# ComboBox 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ComboBox> 控制項是用來在下拉式清單方塊中顯示資料。  根據預設，<xref:System.Windows.Forms.ComboBox> 控制項會顯示於兩個部分：上層部分是可讓使用者輸入清單項目的文字方塊。  第二個部分是顯示項目清單的清單方塊，使用者可從中選取一個項目。  如需其他下拉式方塊樣式的詳細資訊，請參閱[何時使用 Windows Form ComboBox 取代 ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)。  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 屬性會傳回對應至選取清單項目的整數值。  您可以變更程式碼中的 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 值，以程式設計方式變更選取的項目；清單中的對應項目將會出現在下拉式方塊的文字方塊部分中。  如果未選取任何項目，<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 值會是 –1。  如果選取清單中的第一個項目，則 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 值則為 0。  <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> 屬性和 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 類似，但它會傳回項目本身，通常為字串值。  <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> 屬性會反映清單的項目數目，而 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> 屬性值永遠比 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 的最大可能值大 1，因為 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 是以零起始的。  
  
 若要在 <xref:System.Windows.Forms.ComboBox> 控制項中加入或刪除項目，請使用 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> 或 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> 方法。  此外，您也可在設計工具中使用 <xref:System.Windows.Forms.ComboBox.Items%2A> 屬性，將項目加入清單中。  
  
## 請參閱  
 <xref:System.Windows.Forms.ComboBox>   
 [ListBox 控制項概觀](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)   
 [何時使用 Windows Form ComboBox 取代 ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [如何：在 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)   
 [如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)   
 [如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)