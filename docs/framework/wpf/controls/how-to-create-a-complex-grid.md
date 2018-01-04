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
ms.workload: dotnet
ms.openlocfilehash: b9dfb913407622f3cbd9a067a94cc6400b501e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="10b71-102">如何：建立複雜格線</span><span class="sxs-lookup"><span data-stu-id="10b71-102">How to: Create a Complex Grid</span></span>
<span data-ttu-id="10b71-103">這個範例示範如何使用<xref:System.Windows.Controls.Grid>來建立每月的行事曆看起來的版面配置。</span><span class="sxs-lookup"><span data-stu-id="10b71-103">This example shows how to use a <xref:System.Windows.Controls.Grid> to create layout that looks like a monthly calendar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10b71-104">範例</span><span class="sxs-lookup"><span data-stu-id="10b71-104">Example</span></span>  
 <span data-ttu-id="10b71-105">下列範例定義了八個資料列和八個資料行使用<xref:System.Windows.Controls.RowDefinition>和<xref:System.Windows.Controls.ColumnDefinition>類別。</span><span class="sxs-lookup"><span data-stu-id="10b71-105">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="10b71-106">它會使用<xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType>和<xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType>附加屬性，並搭配<xref:System.Windows.Shapes.Rectangle>項目，則填滿的各種資料行和資料列的背景。</span><span class="sxs-lookup"><span data-stu-id="10b71-106">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="10b71-107">此設計可，因為每個儲存格中只能存在一個以上的項目<xref:System.Windows.Controls.Grid>，主要差異<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Documents.Table>。</span><span class="sxs-lookup"><span data-stu-id="10b71-107">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>  
  
 <span data-ttu-id="10b71-108">此範例會使用垂直漸層來<xref:System.Windows.Shapes.Shape.Fill%2A>的資料行和資料列，以改進的視覺呈現和行事曆的可讀性。</span><span class="sxs-lookup"><span data-stu-id="10b71-108">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows in order to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="10b71-109">樣式<xref:System.Windows.Controls.TextBlock>項目代表的日期和星期幾。</span><span class="sxs-lookup"><span data-stu-id="10b71-109">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="10b71-110"><xref:System.Windows.Controls.TextBlock>項目絕對定位在它們的儲存格使用<xref:System.Windows.FrameworkElement.Margin%2A>屬性和樣式的應用程式中所定義的對齊屬性。</span><span class="sxs-lookup"><span data-stu-id="10b71-110"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="10b71-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="10b71-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [<span data-ttu-id="10b71-112">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="10b71-112">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="10b71-113">面板概觀</span><span class="sxs-lookup"><span data-stu-id="10b71-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="10b71-114">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="10b71-114">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
