---
title: "如何：錨定 Windows Form 上的控制項 | Microsoft Docs"
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
  - "Anchor 屬性, 啟用可調整大小的表單"
  - "控制項 [Windows Form], 錨定"
  - "控制項 [Windows Form], 位置"
  - "表單, 調整大小"
  - "調整表單大小"
  - "螢幕解析度和控制項顯示"
  - "Windows Form 控制項, 螢幕解析度"
  - "Windows Form 控制項, 大小"
  - "Windows Form, 調整大小"
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：錨定 Windows Form 上的控制項
假如您設計一個表單讓使用者可以在執行階段調整它的大小，那麼表單上的控制項就應適當地重新調整大小和重新放置。  要控制項動態的隨畫面調整大小，您可以用 Windows Form 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性。  <xref:System.Windows.Forms.Control.Anchor%2A> 屬性定義了控制項的錨定位置。  當一個控制項錨定到表單，同時表單重新調整大小，則控制項仍舊維持控制項和錨定位置的距離。  例如，如果您有錨定到表單左邊、右邊和底部邊緣的 <xref:System.Windows.Forms.TextBox> 控制項，則當表單重新調整大小時，<xref:System.Windows.Forms.TextBox> 控制項會重新調整水平大小，如此就能和表單的左邊和右邊維持相同的距離。  除此之外，控制項本身也會做垂直定位，如此它與表單下緣就可維持同樣的距離。  假如控制項未錨定而表單重新調整了大小，那麼控制項相對應於表單邊緣的位置就會改變。  
  
 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性和 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性互動。  如需詳細資訊，請參閱 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在表單上錨定控制項  
  
1.  選取您要錨定的控制項。  
  
    > [!NOTE]
    >  您可以藉由按下 CTRL 鍵，再按一下每個控制項以進行選取，然後遵循此程序的其餘部分來同時錨定多個控制項。  
  
2.  在 \[**屬性**\] 視窗內，按一下 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性右邊的箭頭。  
  
     編輯器顯現並出現一個十字。  
  
3.  要設定一個錨點，按一下十字的上、左、右或底部的部分。  
  
     控制項預設錨定在上部和左邊。  
  
4.  若要清除已錨定的控制項一邊，請按一下十字的相應邊。  
  
5.  若要關閉 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性編輯器，請再按一下 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性名稱。  
  
 當您在執行階段時顯示表單，控制項會重新調整大小，以便維持與表單兩邊同樣的距離。  跟錨定邊緣之間的距離始終維持和控制項放置在 Windows Form 設計工具內定義的距離一樣。  
  
> [!NOTE]
>  某些控制項，例如 <xref:System.Windows.Forms.ComboBox> 控制項，在高度方面會有限制。  將控制項錨定到它表單或容器 \(Container\) 的底部時，並不能夠強迫控制項超過其高度限制。  
  
 繼承控制項必須是 `Protected` 才能夠加以錨定。  若要變更控制項的存取層級，請在 \[**屬性**\] 視窗中設定 `Modifiers` 屬性。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [如何：將控制項停駐在 Windows Form 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)