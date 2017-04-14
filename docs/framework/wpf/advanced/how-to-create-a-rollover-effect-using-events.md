---
title: "如何：使用事件建立變化效果 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "項目色彩, 變更"
  - "項目色彩, 變更"
  - "變換效果"
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用事件建立變化效果
本範例示範如何在滑鼠指標移入及移出項目佔據的區域時，變更該項目的色彩。  
  
 本範例包含一個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案和一個程式碼後置的檔案。  
  
> [!NOTE]
>  本範例示範如何使用事件，但是達成相同效果的建議方式是在樣式中使用 <xref:System.Windows.Trigger>。  如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
## 範例  
 下列 [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] 會建立使用者介面 \(由 <xref:System.Windows.Controls.TextBlock> 周圍的 <xref:System.Windows.Controls.Border> 組成\)，並將 <xref:System.Windows.Input.Mouse.MouseEnter> 和 <xref:System.Windows.UIElement.MouseLeave> 事件處理常式附加至 <xref:System.Windows.Controls.Border>。  
  
 [!code-xml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.MouseEnter> 和 <xref:System.Windows.UIElement.MouseLeave> 事件處理常式。  當滑鼠指標移入 <xref:System.Windows.Controls.Border> 時，<xref:System.Windows.Controls.Border> 的背景會變成紅色。  當滑鼠指標移出 <xref:System.Windows.Controls.Border> 時，<xref:System.Windows.Controls.Border> 的背景就會變回白色。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]