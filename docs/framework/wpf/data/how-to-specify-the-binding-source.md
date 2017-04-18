---
title: "如何：指定繫結來源 | Microsoft Docs"
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
  - "資料繫結, 繫結來源"
  - "繫結來源"
  - "資料繫結, 繫結來源"
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：指定繫結來源
在資料繫結中，[繫結來源](GTMT)物件是指您的資料取得來源物件。  本主題說明指定[繫結來源](GTMT)的不同方式。  
  
## 範例  
 如果您將數個屬性繫結至同一個來源，要使用 `DataContext` 屬性，它是建立範圍的便利方式，在這個範圍中所有資料繫結屬性都繼承同一個來源。  
  
 下列範例會在應用程式的根項目建立資料內容。  這會使所有子項目都繼承這個資料內容。  繫結的資料來自自訂的資料類別 `NetIncome`，這個類別是直接透過對應受到參考，並且具有資源索引鍵 `incomeDataSource`。  
  
 [!code-xml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 下列範例顯示 `NetIncome` 類別的定義。  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  上述範例在標記中產生執行個體，並用它當資源。  如果您想繫結至已在程式碼中具現化 \(Instantiate\) 的執行個體物件，必須以程式設計的方式設定 `DataContext` 屬性。  如需範例，請參閱 [讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)。  
  
 或者，如果您想明確指定個別繫結的來源，則有以下選擇。  這些屬性優先於繼承的資料內容。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.Windows.Data.Binding.Source%2A>|使用這個屬性將來源設定為某個物件執行個體。  如果您不需要範圍建立功能以使這個範圍中的數個屬性都繼承同一資料內容，可以使用 <xref:System.Windows.Data.Binding.Source%2A> 屬性來代替 `DataContext` 屬性。  如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.Source%2A>。|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|當您想以相對於[繫結目標](GTMT)的位置指定來源，這十分有用。  使用這個屬性的常見案例是，當您想將項目的一個屬性繫結至同一項目的其他屬性時，或當您正在樣式或範例中定義繫結時。  如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.RelativeSource%2A>。|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|指定一個字串來代表您想繫結至的項目。  當您想要繫結至應用程式中其他項目的屬性時，這十分有用。  例如，如果您想使用 <xref:System.Windows.Controls.Slider> 控制應用程式中另一個控制項的高度，或者想將控制項的 <xref:System.Windows.Controls.ContentControl.Content%2A> 繫結至您 <xref:System.Windows.Controls.ListBox> 控制項的 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性。  如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.ElementName%2A>。|  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=fullName>   
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=fullName>   
 [屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [繫結宣告概觀](../../../../docs/framework/wpf/data/binding-declarations-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)