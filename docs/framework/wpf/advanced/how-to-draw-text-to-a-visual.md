---
title: "如何：繪製文字至視覺效果 | Microsoft Docs"
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
  - "繪製, 文字至視覺效果"
  - "文字, 繪製至視覺效果"
  - "印刷樣式, 將文字繪製至視覺效果"
  - "視覺效果, 將文字繪製至"
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：繪製文字至視覺效果
下列範例顯示如何使用 <xref:System.Windows.Media.DrawingContext> 物件將文字繪製到 <xref:System.Windows.Media.DrawingVisual>。  呼叫 <xref:System.Windows.Media.DrawingVisual> 物件的 <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> 方法，即可傳回繪圖內容。  您可以將圖形和文字繪製到繪圖內容中。  
  
 若要繪製文字到繪圖內容，請使用 <xref:System.Windows.Media.DrawingContext> 物件的 <xref:System.Windows.Media.DrawingContext.DrawText%2A> 方法。  將內容繪製到繪圖內容後，請呼叫 <xref:System.Windows.Media.DrawingContext.Close%2A> 方法，以關閉繪圖內容和保存此內容。  
  
## 範例  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  如需擷取上述程式碼範例之來源的完整程式碼範例，請參閱[使用 DrawingVisual 進行點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159994) \(英文\)。