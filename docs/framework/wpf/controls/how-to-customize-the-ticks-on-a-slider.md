---
title: "如何：自訂滑桿上的刻度 | Microsoft Docs"
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
  - "TickBar"
  - "滑桿控制項，使用 TickBar 建立"
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：自訂滑桿上的刻度
這個範例示範如何建立<xref:System.Windows.Controls.Slider>具有刻度標記的控制項。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Primitives.TickBar>顯示當您設定<xref:System.Windows.Controls.Slider.TickPlacement%2A>屬性以外的值為<xref:System.Windows.Controls.Primitives.TickPlacement>，這是預設值。  
  
 下列範例示範如何建立<xref:System.Windows.Controls.Slider>與<xref:System.Windows.Controls.Primitives.TickBar>顯示刻度。 <xref:System.Windows.Controls.Slider.TickPlacement%2A>和<xref:System.Windows.Controls.Slider.TickFrequency%2A>屬性，定義刻度標記與它們之間的間隔的位置。 當您移動<xref:System.Windows.Controls.Primitives.Thumb>，工具提示會顯示的值<xref:System.Windows.Controls.Slider>。 <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>屬性會定義工具提示會發生。 <xref:System.Windows.Controls.Primitives.Thumb>移動對應到刻度的位置，因為<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>設為`true`。  
  
 下列範例示範如何使用<xref:System.Windows.Controls.Slider.Ticks%2A>屬性來建立刻度標記沿著<xref:System.Windows.Controls.Slider>不規則的間隔。  
  
 [!code-xml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Slider>   
 <xref:System.Windows.Controls.Primitives.TickBar>   
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>   
 [滑桿的如何主題](http://msdn.microsoft.com/zh-tw/534be86c-afb2-425d-8186-631278a9925e)