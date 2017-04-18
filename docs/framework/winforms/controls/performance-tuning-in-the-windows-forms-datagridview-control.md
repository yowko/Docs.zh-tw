---
title: "Windows Form DataGridView 控制項中的效能微調 | Microsoft Docs"
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
  - "DataGridView 控制項 [Windows Form], 效能調整"
  - "效能調整, 資料格"
  - "效能, DataGridView 控制項"
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows Form DataGridView 控制項中的效能微調
在處理大量資料時，`DataGridView` 控制項經常會耗用大量的記憶體，除非您謹慎使用。  在記憶體有限的用戶端上，您可以避免使用會佔用大量記憶體的功能，來避免一些這樣的負荷。  您也可以使用虛擬模式來自行管理一些或全部的資料維護和擷取工作，為您的案例自訂記憶體使用量。  
  
## 在本節中  
 [縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 描述如何在使用大量資料時，以能夠避免不必要的記憶體使用量和效能損失的方式來使用 `DataGridView` 控制項。  
  
 [Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 描述如何使用虛擬模式以補充或取代標準的資料繫結機制。  
  
 [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 描述如何為幾個虛擬模式事件實作處理常式。  同時，也示範如何為使用者編輯作業實作資料列層級的復原和認可。  
  
 [在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 描述如何依照需求載入資料，這在要顯示的資料超過用戶端記憶體的可儲存量時非常有用。  
  
## 參考  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 提供 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性的參考文件。  
  
## 請參閱  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows Form DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)