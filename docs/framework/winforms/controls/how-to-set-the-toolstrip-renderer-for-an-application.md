---
title: "如何：設定應用程式的 ToolStrip 產生器 | Microsoft Docs"
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
  - "Renderer 屬性 [Windows Form]"
  - "工具列 [Windows Form], 自訂"
  - "ToolStrip 控制項 [Windows Forms]"
  - "ToolStripProfessionalRenderer 類別 [Windows Form]"
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：設定應用程式的 ToolStrip 產生器
您可以針對個別的 <xref:System.Windows.Forms.ToolStrip> 控制項，或是應用程式中的所有 <xref:System.Windows.Forms.ToolStrip> 控制項自訂外觀。  
  
## 範例  
 下列程式碼範例示範如何選擇性地將自訂轉譯器套用至 <xref:System.Windows.Forms.ToolStrip> 控制項和 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
 若要使用此程式碼範例，請編譯並執行應用程式，然後從 <xref:System.Windows.Forms.ComboBox> 控制項選取自訂轉譯的範圍。  按一下 \[套用\] 以設定轉譯器。  
  
 若要查看自訂功能表項目轉譯，請從 <xref:System.Windows.Forms.MenuStrip> 控制項選取 <xref:System.Windows.Forms.ComboBox> 選項，按一下 \[套用\]，然後開啟 \[檔案\] 功能表項目。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 設定 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> 屬性，以將自訂轉譯器套用至應用程式中的所有 <xref:System.Windows.Forms.ToolStrip> 控制項。  
  
 設定 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> 屬性，以將自訂轉譯器套用至個別的 <xref:System.Windows.Forms.ToolStrip> 控制項。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripManager>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)