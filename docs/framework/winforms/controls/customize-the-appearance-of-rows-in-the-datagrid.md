---
title: "如何：在 Windows Form DataGridView 控制項中自訂資料列的外觀 | Microsoft Docs"
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
  - "資料格, 自訂資料列"
  - "DataGridView 控制項 [Windows Form], 自訂資料列"
  - "資料列, 在 DataGridView 控制項中自訂"
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：在 Windows Form DataGridView 控制項中自訂資料列的外觀
您可以藉由處理一個或兩個 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName> 和 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName> 事件，來控制 <xref:System.Windows.Forms.DataGridView> 資料列的外觀 。  這些事件經過設計，以便您可以在 <xref:System.Windows.Forms.DataGridView> 控制項繪製其餘部分的時候只繪製您想要的部分。  例如，如果您想要繪製自訂背景，您可以處理 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName> 事件，然後讓個別儲存格繪製自己的前景內容。  或者，您可以讓儲存格繪製自己，並加入自訂前景內容到 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName> 事件的處理常式。  您也可以停用儲存格繪製，自行在 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName> 事件處理常式中繪製全部內容。  
  
 下列程式碼範例會實作兩個事件的處理常式，以提供漸層選取背景和某些跨越多個資料行的自訂前景內容。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName>   
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)