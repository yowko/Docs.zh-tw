---
title: "如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DoubleBuffered 屬性"
  - "重繪閃動, 在 Windows Form 中減少"
  - "圖形, 減少雙重緩衝的重繪閃動"
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動
雙重緩衝會使用記憶體緩衝區，解決因多重繪製作業所造成的閃動問題。  啟用雙重緩衝時，所有的繪製作業會先呈現在記憶體緩衝區中，而不是先描繪在螢幕上。  當所有繪製作業都完成時，就會直接將記憶體緩衝區複製到與其相關聯的繪圖介面，  因為螢幕上只執行一個圖形作業，便能夠排除因複雜的繪製作業所造成的影像閃動問題。對大部分應用程式而言，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 所提供的預設雙重緩衝就可以提供最佳結果。  標準 Windows Form 控制項預設就會進行雙重緩衝。  您可以使用兩種方式在表單和已編寫的控制項中啟用預設雙重緩衝：  一個方式是將 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設為 `true`，另一個方式則是呼叫 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法將 <xref:System.Windows.Forms.ControlStyles> 旗標設為 `true`。  這兩種方式都可以啟用表單或控制項的預設雙重緩衝，並提供不會閃動的圖形呈現方式。  呼叫 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法只建議用於您已經編寫了所有呈現程式碼的自訂控制項。  
  
 如果是比較進階的雙重緩衝狀況，例如動畫或進階記憶體管理，您可以實作自己的雙重緩衝邏輯。  如需詳細資訊，請參閱 [如何：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)。  
  
### 若要減少閃動的情況  
  
-   將 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設定為 `true`  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \-或\-  
  
-   呼叫 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法將 <xref:System.Windows.Forms.ControlStyles> 旗標設定為 `true`  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>   
 <xref:System.Windows.Forms.Control.SetStyle%2A>   
 [雙重緩衝的圖形](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)