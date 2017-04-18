---
title: "如何：繫結兩個控制項的屬性 | Microsoft Docs"
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
  - "繫結兩個控制項的屬性"
  - "控制項, 繫結屬性"
  - "資料繫結, 繫結兩個控制項的屬性"
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：繫結兩個控制項的屬性
這個範例顯示如何使用 <xref:System.Windows.Data.Binding.ElementName%2A> 屬性，將一個具現化 \(Instantiated\) 控制項的屬性繫結至另一個控制項的屬性。  
  
## 範例  
 下列範例顯示如何將 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Panel.Background%2A> 屬性繫結至 <xref:System.Windows.Controls.ComboBox> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> 屬性：  
  
 [!code-xml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 這個範例在轉譯後，會與下列類似：  
  
 ![具有綠色背景的畫布](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.png "DataBindingBindingDPsSample")  
  
 **注意** [繫結目標](GTMT)屬性 \(在這個範例中是 <xref:System.Windows.Controls.Panel.Background%2A> 屬性\) 必須是[相依性屬性](GTMT)。  如需詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
## 請參閱  
 [指定繫結來源](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)