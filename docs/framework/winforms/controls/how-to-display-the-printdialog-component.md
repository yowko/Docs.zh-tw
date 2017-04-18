---
title: "如何：顯示 PrintDialog 元件 | Microsoft Docs"
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
  - "列印對話方塊, 顯示"
  - "PrintDialog 元件 [Windows Form], 顯示"
  - "列印 [Windows Form], 顯示列印對話方塊"
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：顯示 PrintDialog 元件
<xref:System.Windows.Forms.PrintDialog> 元件是許多使用者都相當熟悉的標準 Windows 列印對話方塊。  由於您的使用者能夠很快地上手，所以使用 <xref:System.Windows.Forms.PrintDialog> 元件對您應該佷有幫助。  
  
### 若要顯示 PrintDialog 元件  
  
-   在應用程式的程式碼中呼叫 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法。  
  
     顯示元件後，使用者將與其互動，設定列印工作的屬性。  這些都會儲存在與該列印工作關聯的 [PrinterSettings](frlrfSystemDrawingPrintingPrinterSettingsMembersTopic) 類別 \(以及 [PageSettings](frlrfSystemDrawingPrintingPageSettingsMembersTopic) 類別，如果使用者是透過 <xref:System.Windows.Forms.PrintDialog> 元件存取 [PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)\)。  接著您可以呼叫用來決定列印工作特性的屬性。  
  
## 請參閱  
 [如何：建立標準的 Windows Form 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)   
 [如何：在執行階段從 PrintDialog 擷取使用者輸入](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)   
 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)