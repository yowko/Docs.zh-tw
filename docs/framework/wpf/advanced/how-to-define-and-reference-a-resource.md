---
title: "如何：定義和參考資源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173be3048f7bf082db2eef2ea21eb1e0319f9a43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-reference-a-resource"></a>如何：定義和參考資源
這個範例示範如何定義資源，並使用中的屬性來參考該[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
## <a name="example"></a>範例  
 下列範例會定義兩種資源類型：<xref:System.Windows.Media.SolidColorBrush>資源，以及數個<xref:System.Windows.Style>資源。 <xref:System.Windows.Media.SolidColorBrush>資源`MyBrush`用來提供數個屬性的值，每個接受<xref:System.Windows.Media.Brush>輸入值。 <xref:System.Windows.Style>資源`PageBackground`，`TitleText`和`Label`每個目標特定控制項類型。 樣式的各種不同的屬性時上設定目標的控制項，該樣式資源資源索引鍵所參考，且用來設定<xref:System.Windows.FrameworkElement.Style%2A>數個特定的控制項項目中定義的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 中的 setter 屬性的一個附註`Label`樣式也會參考`MyBrush`先前定義的資源。 這是常見的技術，但請務必記住，資源會剖析並輸入的資源字典中指定的順序。 如果您使用字典中找到的順序也要求資源[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)參考從另一個資源內。 請確定您參考的任何資源先前定義的資源集合比該資源都在要求中。 如果有必要，您可以解決的資源 refererences 嚴格的建立順序使用[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)相反地，參考這個資源，在執行階段，但您應該注意，此 DynamicResource方法會影響效能。 如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
