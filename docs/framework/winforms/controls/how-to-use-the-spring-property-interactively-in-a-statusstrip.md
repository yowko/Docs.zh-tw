---
title: "如何：在 StatusStrip 中以互動方式使用 Spring 屬性 | Microsoft Docs"
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
  - "Spring 屬性 [Windows Form]"
  - "狀態列, 範例"
  - "StatusStrip 控制項 [Windows Form]"
  - "ToolStrip 控制項 [Windows Forms]"
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 StatusStrip 中以互動方式使用 Spring 屬性
您可以使用 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性，將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項放置在 <xref:System.Windows.Forms.StatusStrip> 控制項中。  <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性會判斷 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項是否會自動填滿 <xref:System.Windows.Forms.StatusStrip> 控制項上的可用空間。  
  
## 範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性，將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項放置在 <xref:System.Windows.Forms.StatusStrip> 控制項中。  <xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式會執行 Exclusive\-OR \(XOR\) 運算，以切換 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性的值。  
  
 若要使用這個程式碼範例，請編譯並執行應用程式，然後按一下 <xref:System.Windows.Forms.StatusStrip> 控制項上的 \[Middle \(Spring\)\]，以切換 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性的值。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)