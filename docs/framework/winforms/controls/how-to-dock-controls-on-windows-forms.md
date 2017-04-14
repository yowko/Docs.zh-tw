---
title: "如何：將控制項停駐在 Windows Form 上 | Microsoft Docs"
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
  - "控制項 [Windows Form], 停駐"
  - "Dock 屬性"
  - "檔案總管樣式應用程式, 建立"
  - "Windows Form 控制項, 填滿工作區"
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：將控制項停駐在 Windows Form 上
您可將控制項停駐在表單的邊緣或填滿控制項的容器 \(可能是一個表單或是容器控制項\)。  例如，Windows 檔案總管會將其 <xref:System.Windows.Forms.TreeView> 控制項停駐在視窗的左邊，並且將 <xref:System.Windows.Forms.ListView> 控制項停駐在視窗的右邊。  您可以使用 <xref:System.Windows.Forms.Control.Dock%2A> 屬性，為所有可見的 Windows Form 控制項定義停駐模式。  
  
> [!NOTE]
>  控制項會依反向疊置順序 \(Z\-order\) 停駐。  
  
 <xref:System.Windows.Forms.Control.Dock%2A> 屬性和 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性互動。  如需詳細資訊，請參閱 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。  
  
### 若要停駐控制項  
  
1.  選取您要停駐的控制項。  
  
2.  在 \[屬性\] 視窗中，按一下 <xref:System.Windows.Forms.Control.Dock%2A> 屬性右邊的箭頭。  
  
     編輯器隨即出現，並顯示一連串表示表單中間和邊緣部分的方塊。  
  
3.  按一下表示表單邊緣的按鈕，也就是您想要停駐控制項的地方。  若要填滿控制項表單或是容器控制項的內容，請按一下中間方塊。  按一下 \[**\(無\)**\] 停用停駐。  
  
     控制項會自動調整大小以符合停駐邊緣的界限。  
  
    > [!NOTE]
    >  繼承的控制項必須是 `Protected` 才能停駐。  若要變更控制項的存取層級，請在 \[屬性\] 視窗中設定控制項的 \[**Modifier**\] 屬性。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [依功能區分 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)   
 [如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [如何：錨定 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)