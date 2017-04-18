---
title: "ListBox 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "ListBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "清單方塊, 關於清單方塊"
  - "ListBox 控制項 [Windows Form], 關於 ListBox 控制項"
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ListBox 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ListBox> 控制項會顯示清單來讓使用者從中選取一或多個項目。  如果項目的總數超過可顯示的數目，則捲軸會自動加入至 <xref:System.Windows.Forms.ListBox> 控制項。  將 <xref:System.Windows.Forms.ListBox.MultiColumn%2A> 屬性設定為 `true` 時，清單方塊會以多欄方式顯示項目，這時會出現水平捲軸。  將 <xref:System.Windows.Forms.ListBox.MultiColumn%2A> 屬性設定為 `false` 時，清單方塊會以單欄方式顯示項目，這時會出現垂直捲軸。  將 <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> 設定為 `true` 時，則不管項目數為何，都會出現捲軸。  <xref:System.Windows.Forms.ListBox.SelectionMode%2A> 屬性決定一次可選取的清單項目數量。  
  
## ListBox 控制項的變更方法  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 屬性會傳回整數，此整數對應至清單方塊中的第一個選取項目。  您可以在程式碼中變更 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值，用程式設計來變更選取的項目；清單中的對應項目將反白顯示出現在 Windows Form 上。  如果未選取任何項目，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值會是 –1。  如果選取清單中的第一個項目，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值就會是 0。  當選取多個項目時，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值會反映最先出現在清單中的選取項目。  <xref:System.Windows.Forms.ListBox.SelectedItem%2A> 屬性和 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 類似，但它會傳回項目本身，通常為字串值。  <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> 屬性會反映清單中項目的數目，而且 <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> 屬性值永遠比最大可能的 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值多 1，因為 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 是以零起始的。  
  
 若要在 <xref:System.Windows.Forms.ListBox> 控制項中加入或刪除項目，請使用 <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>、<xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>、<xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> 或 <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> 方法。  此外，您也可在設計階段使用 <xref:System.Windows.Forms.ListBox.Items%2A> 屬性，將項目加入清單中。  
  
## 請參閱  
 <xref:System.Windows.Forms.ListBox>   
 [如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)   
 [ComboBox 控制項概觀](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)   
 [CheckedListBox 控制項概觀](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)   
 [如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)