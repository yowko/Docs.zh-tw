---
title: "如何：將控制項和表單邊緣對齊 | Microsoft Docs"
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
  - "控制項 [Windows Form], 表單上對齊"
  - "自訂控制項 [Windows Form], 使用程式碼停駐"
  - "Dock 屬性, 對齊控制項 (使用程式碼)"
  - "表單, 對齊控制項"
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：將控制項和表單邊緣對齊
您可設定 <xref:System.Windows.Forms.Control.Dock%2A> 屬性讓控制項對齊表單邊緣。  這個屬性會指定您的控制項在表單中的位置。  可將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為下列值：  
  
|設定值|對控制項的影響|  
|---------|-------------|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單下方。|  
|<xref:System.Windows.Forms.DockStyle>|填滿表單中剩下的空間。|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單左方。|  
|<xref:System.Windows.Forms.DockStyle>|不會停駐在任何地方，且會出現在 <xref:System.Windows.Forms.Control.Location%2A> 屬性所指定的位置。|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單右方。|  
|<xref:System.Windows.Forms.DockStyle>|停駐在表單上方。|  
  
 Visual Studio 中有針對此功能提供的設計階段支援。  
  
### 在執行階段設定控制項的 Dock 屬性  
  
1.  在程式碼中，將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為適當值。  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)