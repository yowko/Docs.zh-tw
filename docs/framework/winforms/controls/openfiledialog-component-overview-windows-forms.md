---
title: "OpenFileDialog 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "OpenFileDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "開啟檔案對話方塊, 在 Windows Form 中顯示"
  - "OpenFileDialog 元件, 關於 OpenFileDialog"
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# OpenFileDialog 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.OpenFileDialog> 元件是預先設定的對話方塊。  它與 Windows 作業系統所公開 \(Expose\) 的 \[**開啟檔案**\] 對話方塊是相同的對話方塊，  繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。  
  
## 使用這個元件  
 在您的 Windows 應用程式中使用這個元件來做為檔案選擇的簡單方案，您就不用設定自己的對話方塊。  利用標準的 Windows 對話方塊做為基礎，您可以建立使用者可立即熟悉基本功能的應用程式。  但是請注意，當使用 <xref:System.Windows.Forms.OpenFileDialog> 元件時，您必須撰寫自己的檔案開啟邏輯。  
  
 您可以使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法在執行階段顯示對話方塊，  也可以使用 <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> 屬性讓使用者複選要開啟的檔案。  此外，您還可以使用 <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> 屬性，決定對話方塊中是否要出現唯讀核取方塊。  <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> 屬性表示唯讀核取方塊是否已選取。  最後，<xref:System.Windows.Forms.FileDialog.Filter%2A> 屬性會設定目前檔名的篩選字串，用來決定對話方塊中出現在 \[檔案類型\] 方塊中的選擇。  
  
 當 <xref:System.Windows.Forms.OpenFileDialog> 元件加入表單時，它會出現在 \[Windows Form 設計工具\] 下方的匣中。  
  
## 請參閱  
 <xref:System.Windows.Forms.OpenFileDialog>   
 [OpenFileDialog 元件](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)