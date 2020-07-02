---
title: 如何：使用 XAML 排序和分組資料
description: 瞭解如何建立資料集合的視圖，以便在 Windows Presentation Foundation （WPF）中進行分組、排序和篩選。
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621674"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="fb9e4-103">如何：使用 XAML 排序和分組資料</span><span class="sxs-lookup"><span data-stu-id="fb9e4-103">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="fb9e4-104">這個範例示範如何在中建立資料集合的視圖 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fb9e4-104">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="fb9e4-105">Views 允許群組、排序、篩選和目前專案的概念等功能。</span><span class="sxs-lookup"><span data-stu-id="fb9e4-105">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb9e4-106">範例</span><span class="sxs-lookup"><span data-stu-id="fb9e4-106">Example</span></span>  
 <span data-ttu-id="fb9e4-107">在下列範例中，名為「*位置*」的靜態資源會定義為「*位置*」物件的集合，其中每個「*位置*」物件都是由「城市」名稱和「州」（city）組成。</span><span class="sxs-lookup"><span data-stu-id="fb9e4-107">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="fb9e4-108">前置詞*src*會對應至定義資料來源*位置*所在的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fb9e4-108">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="fb9e4-109">*Scm*對應到 `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` 和*dat*對應的首碼 `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` 。</span><span class="sxs-lookup"><span data-stu-id="fb9e4-109">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="fb9e4-110">下列範例會建立依城市名稱排序並依州/省分組之資料集合的視圖。</span><span class="sxs-lookup"><span data-stu-id="fb9e4-110">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="fb9e4-111">然後，此視圖可以是系結來源，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fb9e4-111">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="fb9e4-112">如需在資源中定義的 XML 資料系結 <xref:System.Windows.Data.XmlDataProvider> ，請在 XML 名稱前面加上 @ 符號。</span><span class="sxs-lookup"><span data-stu-id="fb9e4-112">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="fb9e4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb9e4-113">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="fb9e4-114">取得資料集合的預設視圖</span><span class="sxs-lookup"><span data-stu-id="fb9e4-114">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="fb9e4-115">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="fb9e4-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="fb9e4-116">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="fb9e4-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
