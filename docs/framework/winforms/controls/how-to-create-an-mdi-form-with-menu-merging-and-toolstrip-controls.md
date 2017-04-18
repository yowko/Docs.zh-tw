---
title: "如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單 | Microsoft Docs"
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
  - "MenuStrip 控制項 [Windows Form]"
  - "工具列 [Windows Form]"
  - "ToolStrip 控制項 [Windows Forms]"
  - "ToolStripPanel 控制項 [Windows Form]"
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
<xref:System.Windows.Forms?displayProperty=fullName> 命名空間支援多重文件介面 \(MDI\) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。  MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。  
  
 在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中對這項功能有廣泛的支援。  
  
 另請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](http://msdn.microsoft.com/library/ms233676%20\(v=vs.110\))。  
  
## 範例  
 下列程式碼範例示範如何在 MDI 表單上使用 <xref:System.Windows.Forms.ToolStripPanel> 控制項。  這個表單也支援子功能表的功能表合併。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 這個程式碼範例需要：  
  
-   System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)