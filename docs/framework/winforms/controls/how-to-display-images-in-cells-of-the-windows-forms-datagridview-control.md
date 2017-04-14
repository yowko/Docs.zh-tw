---
title: "如何：顯示 Windows Form DataGridView 控制項的儲存格影像 | Microsoft Docs"
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
  - "儲存格, 顯示影像"
  - "資料格, 顯示儲存格中的影像"
  - "資料格, 顯示在方格內"
  - "DataGridView 控制項 [Windows Form], 顯示影像"
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：顯示 Windows Form DataGridView 控制項的儲存格影像
圖片或圖形是您可以顯示於資料的資料列中的其中一個值。  這些圖形的格式經常是員工的照片或公司標誌。  
  
 顯示 <xref:System.Windows.Forms.DataGridView> 控制項中的資料時，加入圖片很簡單。  <xref:System.Windows.Forms.DataGridView> 控制項原本處理由 <xref:System.Drawing.Image> 類別所支援的任何影像格式，以及由某些資料庫使用的 OLE 圖片格式。  
  
 如果 <xref:System.Windows.Forms.DataGridView> 控制項的資料來源具有影像的資料行，就會由 <xref:System.Windows.Forms.DataGridView> 控制項自動顯示。  
  
 下列程式碼範例示範如何從內嵌資源抽取圖示，並將它轉換為點陣圖，顯示於影像資料行的每一個儲存格。  如需以對應的影像取代文字儲存格值的其他範例，請參閱 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   名為 `tree.ico` 的內嵌圖示資源。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName> 和 <xref:System.Drawing?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)