---
title: "SaveFileDialog 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "SaveFileDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "儲存對話方塊, 顯示"
  - "SaveFileDialog 元件, 關於 SaveFileDialog"
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# SaveFileDialog 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.SaveFileDialog> 元件是預先設定的對話方塊。  它與 Windows 使用的標準 \[**儲存檔案**\] 對話方塊是相同的對話方塊。  繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。  
  
## 使用 SaveFileDialog 元件  
 使用此元件做為使用者儲存檔案的簡單方案，您就不用設定自己的對話方塊。  利用標準的 Windows 對話方塊做為基礎，您可以建立使用者可立即熟悉基本功能的應用程式。  但是請注意，當使用 <xref:System.Windows.Forms.SaveFileDialog> 元件時，您必須撰寫自己的檔案儲存邏輯。  
  
 您可以使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行階段顯示對話方塊。  您也可以使用 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法，在讀取\/寫入模式中開啟檔案。  
  
 當 <xref:System.Windows.Forms.SaveFileDialog> 元件加入表單時，它會出現在 \[Windows Form 設計工具\] 下方的匣中。  
  
## 請參閱  
 <xref:System.Windows.Forms.SaveFileDialog>   
 [SaveFileDialog 元件](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)