---
title: "如何：裝飾 Panel 的子系 | Microsoft Docs"
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
  - "Adorner, 繫結至面板的子系"
  - "Panel 控制項, 將裝飾項繫結至子系"
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：裝飾 Panel 的子系
本範例示範如何以程式設計的方式，將裝飾項繫結至指定之 <xref:System.Windows.Controls.Panel> 的子系。  
  
## 範例  
 若要將裝飾項繫結至 <xref:System.Windows.Controls.Panel> 的子系，請遵循下列步驟：  
  
1.  宣告新的 <xref:System.Windows.Documents.AdornerLayer> 物件，並呼叫 `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 方法，以尋找其子系要進行裝飾之項目的裝飾項層。  
  
2.  列舉父項目的所有子系並呼叫 <xref:System.Windows.Documents.AdornerLayer.Add%2A> 方法，將裝飾項繫結至每個子項目。  
  
 下列範例會將 SimpleCircleAdorner \(如上所示\) 繫結至名稱為 *myStackPanel* 之 <xref:System.Windows.Controls.StackPanel> 的子系。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  目前不支援使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個項目。  
  
## 請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)