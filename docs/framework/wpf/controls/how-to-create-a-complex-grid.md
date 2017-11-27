---
title: "如何：建立複雜格線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c0008a7379feefd9b3fe719f85b3205a72fb51d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-complex-grid"></a>如何：建立複雜格線
這個範例示範如何使用<xref:System.Windows.Controls.Grid>來建立每月的行事曆看起來的版面配置。  
  
## <a name="example"></a>範例  
 下列範例定義了八個資料列和八個資料行使用<xref:System.Windows.Controls.RowDefinition>和<xref:System.Windows.Controls.ColumnDefinition>類別。 它會使用<xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType>和<xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType>附加屬性，並搭配<xref:System.Windows.Shapes.Rectangle>項目，則填滿的各種資料行和資料列的背景。 此設計可，因為每個儲存格中只能存在一個以上的項目<xref:System.Windows.Controls.Grid>，主要差異<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Documents.Table>。  
  
 此範例會使用垂直漸層來<xref:System.Windows.Shapes.Shape.Fill%2A>的資料行和資料列，以改進的視覺呈現和行事曆的可讀性。 樣式<xref:System.Windows.Controls.TextBlock>項目代表的日期和星期幾。 <xref:System.Windows.Controls.TextBlock>項目絕對定位在它們的儲存格使用<xref:System.Windows.FrameworkElement.Margin%2A>屬性和樣式的應用程式中所定義的對齊屬性。  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)
