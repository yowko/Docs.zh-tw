---
title: "如何：建立專業樣式的 ToolStrip 控制項 | Microsoft Docs"
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
  - "工具列 [Windows Form]"
  - "ToolStrip 控制項 [Windows Forms]"
  - "ToolStripProfessionalRenderer 類別 [Windows Form]"
  - "ToolStripRenderer 類別 [Windows Form]"
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立專業樣式的 ToolStrip 控制項
您可以藉由自行撰寫衍生自 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類型的類別，賦與應用程式的 <xref:System.Windows.Forms.ToolStrip> 控制項專業外觀和行為 \(外觀及操作\)。  
  
 在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中對這項功能有廣泛的支援。  
  
 請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md)。  
  
## 範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStrip> 控制項建立複合控制項，以模擬 Microsoft® Outlook® 提供的 \[瀏覽窗格\]。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](http://msdn.microsoft.com/library/ms233664%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [如何：對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)