---
title: "如何：根據繫結項目的清單產生值 | Microsoft Docs"
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
  - "資料繫結, MultiBinding"
  - "MultiBinding"
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：根據繫結項目的清單產生值
<xref:System.Windows.Data.MultiBinding> 可讓您將[繫結目標](GTMT)屬性 \(Property\) 繫結至來源屬性清單，然後套用邏輯以用這些輸入產生一個值。  這個範例會示範 <xref:System.Windows.Data.MultiBinding> 的用法。  
  
## 範例  
 在下列範例中，`NameListData` 參考 `PersonName` 物件的集合，這些物件都包含兩個屬性 \(Property\)：`firstName` 和 `lastName`。  下列範例產生的 <xref:System.Windows.Controls.TextBlock> 會顯示一個人的名字和姓氏，先列出姓氏再列出名字。  
  
 [!code-xml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 為了要了解名字\-姓氏這樣的格式是如何產生，我們一起看看 `NameConverter` 的實作：  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` 會實作 <xref:System.Windows.Data.IMultiValueConverter> 介面。  `NameConverter` 會從個別繫結取得值，然後將這些值儲存在 values 物件陣列中。  在 <xref:System.Windows.Data.MultiBinding> 項目下的 <xref:System.Windows.Data.Binding> 項目出現順序，就是這些值在陣列中的儲存順序。  <xref:System.Windows.Data.MultiBinding.Converter%2A> 方法的 parameter 引數會參考 <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> 屬性 \(Attribute\) 的值，這個方法會對參數執行開關，以決定姓名的格式。  
  
## 請參閱  
 [轉換繫結的資料](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)