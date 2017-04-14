---
title: "如何：以互動方式控制時鐘 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "時鐘, 用互動方式控制"
  - "用互動方式控制時鐘"
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：以互動方式控制時鐘
<xref:System.Windows.Media.Animation.Clock> 物件的 <xref:System.Windows.Media.Animation.ClockController> 屬性可以讓您以互動方式啟動時鐘、暫停時鐘、繼續時鐘、搜尋時鐘、前進到時鐘的填滿時間，以及停止時鐘。  只有時間樹狀結構的根時鐘可以互動方式控制。  
  
> [!NOTE]
>  有其他方式可以互動方式控制動畫，而不需要直接處理時鐘：您也可以使用腳本。  在標記和程式碼中都支援腳本。  如需範例，請參閱 [使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)或[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 下列範例會使用數種按鈕以互動方式控制動畫時鐘。  
  
## 範例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## 請參閱  
 [使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)