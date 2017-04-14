---
title: "如何：繫結至列舉 | Microsoft Docs"
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
  - "資料繫結, 列舉"
  - "資料繫結, 列舉"
  - "列舉"
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：繫結至列舉
本範例示範如何透過繫結至列舉型別的 GetValues 方法，繫結到列舉型別。  
  
## 範例  
 在下列範例中，<xref:System.Windows.Controls.ListBox> 會顯示整個資料繫結中 <xref:System.Windows.HorizontalAlignment> 列舉值的清單。  <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.Button> 已經繫結在一起，您只要從 <xref:System.Windows.Controls.ListBox> 中選取一個值，就能變更 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性值。  
  
 [!code-xml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## 請參閱  
 [繫結至方法](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)