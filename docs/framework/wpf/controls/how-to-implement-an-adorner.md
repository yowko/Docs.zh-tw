---
title: "如何：實作裝飾項 | Microsoft Docs"
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
  - "Adorner, 實作"
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：實作裝飾項
此範例示範最小裝飾項的實作。  
  
## 實作器注意事項  
 請特別注意，裝飾項不包含任何繼承呈現行為，以確保裝飾項呈現是裝飾項實作器的職責。  實作呈現行為的常見方式，就是覆寫 <xref:System.Windows.UIElement.OnRender%2A> 方法並視需要使用一個或多個 <xref:System.Windows.Media.DrawingContext> 物件來呈現裝飾項的視覺物件 \(如這個範例所示\)。  
  
## 範例  
  
### 描述  
 實作繼承自抽象 <xref:System.Windows.Documents.Adorner> 類別的類別，即可建立自訂裝飾項。  這個範例裝飾項會覆寫 <xref:System.Windows.UIElement.OnRender%2A> 方法，藉此方式用圓形裝飾 <xref:System.Windows.UIElement> 的角落。  
  
### 程式碼  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## 請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)