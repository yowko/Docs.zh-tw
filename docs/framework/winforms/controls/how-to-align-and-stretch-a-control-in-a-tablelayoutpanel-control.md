---
title: "如何：在 TableLayoutPanel 控制項中對齊和縮放控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form], 對齊"
  - "控制項 [Windows Form], 自動縮放"
  - "TableLayoutPanel 控制項 [Windows Form], 自動縮放控制項"
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：在 TableLayoutPanel 控制項中對齊和縮放控制項
您可以在 <xref:System.Windows.Forms.TableLayoutPanel> 中使用 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 屬性對齊和自動縮放控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要對齊和自動縮放控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  
  
2.  從 \[**工具箱**\] 拖曳 <xref:System.Windows.Forms.Button> 控制項至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左上方儲存格。  <xref:System.Windows.Forms.Button> 控制項是置中於儲存格。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值設定為 `Left,Right`。  <xref:System.Windows.Forms.Button> 控制項會縮放至符合儲存格的寬度。  
  
4.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值設定為 `Top,Bottom`。  <xref:System.Windows.Forms.Button> 控制項會縮放至符合儲存格的高度。  
  
5.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值設定為 <xref:System.Windows.Forms.DockStyle>。  <xref:System.Windows.Forms.Button> 控制項會展開以填滿儲存格。  
  
6.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值設定為 <xref:System.Windows.Forms.DockStyle>。  <xref:System.Windows.Forms.Button> 控制項會回到原始大小，並移至儲存格的左上角。  \[**Windows Form 設計工具**\] 已將 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設定為 `Top, Left`。  
  
7.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值設定為 `Bottom,Right`。  <xref:System.Windows.Forms.Button> 控制項會移至儲存格的右下角。  
  
8.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值設定為 <xref:System.Windows.Forms.AnchorStyles>。  <xref:System.Windows.Forms.Button> 控制項會移至儲存格的中間。  
  
## 請參閱  
 [TableLayoutPanel 控制項](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)