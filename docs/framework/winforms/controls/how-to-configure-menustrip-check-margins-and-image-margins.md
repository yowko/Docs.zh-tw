---
title: "如何：設定 MenuStrip 核取邊界和影像邊界 | Microsoft Docs"
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
  - "邊界, 在 MenuStrip 控制項的設定"
  - "功能表, 設定邊界"
  - "MenuStrip 控制項 [Windows Form], 核取邊界及影像邊界"
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：設定 MenuStrip 核取邊界和影像邊界
您可以用各種組合設定 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> 和 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> 屬性來自訂 <xref:System.Windows.Forms.MenuStrip>。  
  
## 範例  
 下列程式碼範例示範如何設定及自訂 <xref:System.Windows.Forms.ContextMenuStrip> 核取邊界和影像邊界。  用於 <xref:System.Windows.Forms.ContextMenuStrip> 或 <xref:System.Windows.Forms.MenuStrip> 的程序相同。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.ToolStripDropDown>   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [如何：啟用 ContextMenuStrip 控制項中的核取邊界和影像邊界](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)