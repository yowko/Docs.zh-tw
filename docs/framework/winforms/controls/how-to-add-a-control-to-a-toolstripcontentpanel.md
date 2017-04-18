---
title: "如何：將控制項加入 ToolStripContentPanel | Microsoft Docs"
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
  - "ToolStripContentPanel [Windows Form], 加入控制項"
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：將控制項加入 ToolStripContentPanel
您可以程式設計方式將一個或多個控制項加入 <xref:System.Windows.Forms.ToolStripContentPanel>。  
  
## 範例  
 下列程式碼範例示範如何將 <xref:System.Windows.Forms.RichTextBox> 加入 <xref:System.Windows.Forms.ToolStripContentPanel>。  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 這個程式碼範例需要：  
  
-   System、System.Data 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  請同時參閱[如何：使用 Visual Studio 編譯並執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))或 [ToolStripContainer 工作對話方塊](http://msdn.microsoft.com/library/ms233647%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripContentPanel>   
 <xref:System.Windows.Forms.ToolStripContainer>   
 [ToolStripContainer 控制項](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)