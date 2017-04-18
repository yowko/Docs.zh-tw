---
title: "如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容 | Microsoft Docs"
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
  - "CheckedListBox 控制項 [Windows Form], 排序"
  - "下拉式方塊, 排序內容"
  - "ComboBox 控制項 [Windows Form], 排序內容"
  - "清單方塊, 排序內容"
  - "ListBox 控制項 [Windows Form], 排序內容"
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容
Windows Form 控制項在繫結資料時不會排序。  若要顯示排序的資料，請使用支援排序的資料來源，然後讓資料來源予以排序。  支援排序的資料來源有資料檢視、資料檢視管理員和排序陣列。  
  
 如果控制項不是資料繫結控制項，就可以進行排序。  
  
### 若要排序清單  
  
1.  將  `Sorted`  屬性設為 `true`。  
  
     這個設定會依照排序順序重新調整所有現有清單項目的位置。  
  
## 請參閱  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [Windows Form 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [何時使用 Windows Form ComboBox 取代 ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)