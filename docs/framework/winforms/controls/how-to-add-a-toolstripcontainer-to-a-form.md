---
title: "如何：將 ToolStripContainer 加入表單 | Microsoft Docs"
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
  - "工具列 [Windows Form], 內建浮動定位"
  - "ToolStrip 控制項 [Windows Forms], 內建浮動定位"
  - "ToolStripContainer 控制項 [Windows Form], 加入到 Windows Form"
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：將 ToolStripContainer 加入表單
您可以程式設計方式加入 <xref:System.Windows.Forms.ToolStripContainer> 至 Windows Form 並填入控制項。  
  
## 範例  
 下列程式碼範例示範如何加入 <xref:System.Windows.Forms.ToolStripContainer> 和 <xref:System.Windows.Forms.ToolStrip> 至 Windows Form，如何將項目加入 <xref:System.Windows.Forms.ToolStrip>，以及如何加入 <xref:System.Windows.Forms.ToolStrip> 到 <xref:System.Windows.Forms.ToolStripContainer> 的 <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>。  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## 編譯程式碼  
 這個程式碼範例需要：  
  
-   System.Drawing、System.Text 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  請同時參閱[如何：使用 Visual Studio 編譯並執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) 或 [ToolStripContainer 工作對話方塊](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripContainer>   
 [ToolStripContainer 控制項](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)