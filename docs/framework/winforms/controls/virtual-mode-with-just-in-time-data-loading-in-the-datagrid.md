---
title: "如何：在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式 | Microsoft Docs"
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
  - "資料 [Windows Form], 管理大型資料集"
  - "DataGridView 控制項 [Windows Form], 大型資料集"
  - "DataGridView 控制項 [Windows Form], 虛擬模式"
  - "範例 [Windows Form], Just-in-Time 資料載入"
  - "Just-in-Time 資料載入"
  - "虛擬模式, Just-in-Time 資料載入"
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在 Windows Form DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 控制項中的虛擬模式，其中的資料快取只會在需要時才從伺服器載入資料。  這個範例在[在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)中有詳細說明。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Xml 和 System.Windows.Forms 組件的參考。  
  
-   已安裝 Northwind SQL Server 範例資料庫之伺服器的存取權。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## .NET Framework 安全性  
 在連接字串內儲存機密資訊 \(例如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>   
 [在 Windows Form DataGridView 控制項中以 Just\-In\-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)   
 [Windows Form DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)