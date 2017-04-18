---
title: "雙重緩衝的圖形 | Microsoft Docs"
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
  - "雙重緩衝"
  - "範例 [Windows Form], 雙重緩衝的圖形"
  - "重繪閃動, 使用雙重緩衝以減少"
  - "圖形, 雙重緩衝"
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 雙重緩衝的圖形
閃動是編寫圖形程式碼時常見的問題。  需要進行多重複雜繪製作業的圖形作業可能會造成呈現出來的影像看起來閃動不定，或者是呈現出來的樣子讓人無法接受。  為了解決這種問題，.NET Framework 提供了雙重緩衝存取。  
  
 雙重緩衝會使用記憶體緩衝區，解決因多重繪製作業所造成的閃動問題。  啟用雙重緩衝時，所有的繪製作業會先呈現在記憶體緩衝區中，而不是先描繪在螢幕上。  當所有繪製作業都完成時，就會直接將記憶體緩衝區複製到與其相關聯的繪圖介面，  因為螢幕上只執行一個圖形作業，便能夠排除因複雜的繪製作業所造成的影像閃動問題。  
  
## 預設的雙重緩衝  
 在應用程式中使用雙重緩衝最簡單的方法，就是使用表單和控制項預設的雙重緩衝 \(由 .NET Framework 所提供\)。  您可以將 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設定為 `true`，或者是使用 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，藉此啟用 Windows Form 和已編寫的 Windows 控制項的預設雙重緩衝。  如需詳細資訊，請參閱 [如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)。  
  
## 手動管理已緩衝的圖形  
 如果是比較進階的雙重緩衝狀況，例如動畫或進階記憶體管理，您可以使用 .NET Framework 類別實作自己的雙重緩衝邏輯。  負責配置及管理個別圖形緩衝區的類別是 <xref:System.Drawing.BufferedGraphicsContext> 類別。  每一個應用程式定義域都有自己的預設 <xref:System.Drawing.BufferedGraphicsContext> 執行個體，以管理該應用程式所有的預設雙重緩衝。  在大部分情況下，每個應用程式只有一個應用程式定義域，因此每個應用程式一般只有一個預設的 <xref:System.Drawing.BufferedGraphicsContext>。  預設 <xref:System.Drawing.BufferedGraphicsContext> 執行個體是由 <xref:System.Drawing.BufferedGraphicsManager> 類別所控管。  您可以呼叫 [BufferedGraphicsManager.Current 屬性](frlrfSystemDrawingBufferedGraphicsManagerClassCurrentTopic)，藉此擷取預設 <xref:System.Drawing.BufferedGraphicsContext> 執行個體的參考。  您也可以建立專屬的 <xref:System.Drawing.BufferedGraphicsContext> 執行個體，以提高圖形密集的應用程式的效能。  如需如何建立 <xref:System.Drawing.BufferedGraphicsContext> 執行個體的詳細資訊，請參閱 [如何：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)。  
  
## 手動顯示已緩衝的圖形  
 您可以使用 <xref:System.Drawing.BufferedGraphicsContext> 類別的執行個體，經由呼叫 [BufferedGraphicsContext.Allocate 方法](frlrfSystemDrawingBufferedGraphicsContextClassAllocateTopic)建立圖形緩衝區，此方法會傳回 <xref:System.Drawing.BufferedGraphics> 類別的執行個體。  <xref:System.Drawing.BufferedGraphics> 物件會管理和某個呈現介面 \(例如表單或控制項\) 相關聯的記憶體緩衝區。  
  
 當它具現化之後，<xref:System.Drawing.BufferedGraphics> 類別會將圖形的呈現安排至記憶體中圖形緩衝區。  您可以經由 [BufferedGraphics.Graphics 屬性](frlrfSystemDrawingBufferedGraphicsClassGraphicsTopic)將圖形呈現至記憶體緩衝區，此屬性會公開直接代表記憶體緩衝區的 <xref:System.Drawing.Graphics> 物件。  您可以將圖形繪製至這個 <xref:System.Drawing.Graphics> 物件，如同繪製到代表繪圖介面的 <xref:System.Drawing.Graphics> 物件。  當所有圖形都繪製至緩衝區之後，您可以使用 [BufferedGraphics.Render 方法](frlrfSystemDrawingBufferedGraphicsClassRenderTopic)將緩衝區的內容複製到螢幕的繪圖介面上。  
  
 如需使用 <xref:System.Drawing.BufferedGraphics> 類別的詳細資訊，請參閱[手動呈現已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)。  如需呈現圖形的詳細資訊，請參閱 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)。  
  
## 請參閱  
 <xref:System.Drawing.BufferedGraphics>   
 <xref:System.Drawing.BufferedGraphicsContext>   
 <xref:System.Drawing.BufferedGraphicsManager>   
 [如何：手動呈現已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)   
 [如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)   
 [如何：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)