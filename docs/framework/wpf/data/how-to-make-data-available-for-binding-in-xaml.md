---
title: "如何：讓資料可於 XAML 中繫結"
ms.custom: 
ms.date: 01/29/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f4e8e785b246e191ae8052f676331ea116b8c0d
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>如何：讓資料可於 XAML 中繫結
本主題討論您可以將資料繫結中的不同方式[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，視您的應用程式的需求。  
  
## <a name="example"></a>範例  
 如果您有[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件您想要從繫結到[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以將物件提供的繫結是定義為資源，並提供給它的其中一種方式`x:Key`。 在下列範例中，您必須`Person`物件具有名為字串屬性`PersonName`。 `Person`物件，其會顯示包含反白顯示列`<src>`元素，定義在命名空間稱為`SDKSample`。  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 您接著可以繫結<xref:System.Windows.Controls.TextBlock>控制項中的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，如反白顯示列包含`<TextBlock>`項目顯示。 
  
 或者，您可以使用<xref:System.Windows.Data.ObjectDataProvider>類別，如下列範例所示：  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 定義繫結一樣，強調顯示的行會包含`<TextBlock>`項目顯示。  
  
 在這個範例中，結果都相同： 您有<xref:System.Windows.Controls.TextBlock>以文字內容`Joe`。 不過，<xref:System.Windows.Data.ObjectDataProvider>類別提供的功能，例如可以繫結至方法的結果。 您可以選擇使用<xref:System.Windows.Data.ObjectDataProvider>類別，如果您需要它所提供的功能。  
  
 不過，如果您要繫結至已建立的物件，您需要設定`DataContext`在程式碼，如下列範例所示。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料繫結使用<xref:System.Windows.Data.XmlDataProvider>類別，請參閱[XMLDataProvider 和 XPath 查詢來使用 XML 資料繫結](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。 若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料繫結使用<xref:System.Windows.Data.ObjectDataProvider>類別，請參閱[for XML 查詢結果繫結至 XDocument、 XElement 或 LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 如需不同的方式。 您可以指定您要繫結的資料，請參閱[指定繫結來源](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)。 如需哪些資料型別可以繫結或如何實作您自己[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件繫結，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
