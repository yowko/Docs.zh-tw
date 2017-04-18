---
title: "如何：將裝飾項繫結至項目 | Microsoft Docs"
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
  - "Adorner, 繫結至指定的 UIElements"
  - "UIElements, 將裝飾項繫結至"
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：將裝飾項繫結至項目
本範例示範如何以程式設計的方式，將裝飾項繫結至指定的 <xref:System.Windows.UIElement>。  
  
## 範例  
 若要將裝飾項繫結至特定 <xref:System.Windows.UIElement>，請遵循下列步驟：  
  
1.  呼叫 `static` 方法 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 取得 <xref:System.Windows.Documents.AdornerLayer> 物件，以便裝飾 <xref:System.Windows.UIElement>。  <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 會在視覺化樹狀結構中，從指定的 **UIElement** 向上查核，並傳回找到的第一個裝飾項層  \(如果找不到裝飾項層，則方法會傳回 null\)。  
  
2.  呼叫 <xref:System.Windows.Documents.AdornerLayer.Add%2A> 方法，將裝飾項繫結至目標 **UIElement**。  
  
 下列範例會將 SimpleCircleAdorner \(如上所示\) 繫結至名稱為 *myTextBox* 的 <xref:System.Windows.Controls.TextBox>。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  目前不支援使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個項目。  
  
## 請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)