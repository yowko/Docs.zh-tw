---
title: "如何：在設計階段將控制項對齊表單邊緣 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 使用設計工具停駐"
  - "Dock 屬性, 對齊控制項 (使用設計工具)"
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：在設計階段將控制項對齊表單邊緣
您可設定 <xref:System.Windows.Forms.Control.Dock%2A> 讓控制項對齊表單邊緣。  這個屬性會指定您的控制項在表單中的位置。  您可將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為下列值：  
  
|設定|對控制項的影響|  
|--------|-------------|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單下方。|  
|<xref:System.Windows.Forms.DockStyle>|填滿表單中剩下的空間。|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單左方。|  
|<xref:System.Windows.Forms.DockStyle>|不會停駐在任何地方，且會出現在 <xref:System.Windows.Forms.Control.Location%2A> 指定的位置。|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單右方。|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單上方。|  
  
 這些值可在程式碼中設定。  如需詳細資訊，請參閱 [如何：將控制項和表單邊緣對齊](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段設定控制項的 Dock 屬性  
  
1.  在 Windows Form 設計工具中選取您的控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.Control.Dock%2A> 屬性旁的下拉式方塊。  
  
     接著會顯示表示六個可能 <xref:System.Windows.Forms.Control.Dock%2A> 設定的圖形介面。  
  
3.  選擇適當的設定。  
  
4.  這時您的控制項就會依設定指定的方式停駐。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>   
 [如何：將控制項和表單邊緣對齊](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)   
 [逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [如何：錨定 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)   
 [如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [在設計階段開發 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)