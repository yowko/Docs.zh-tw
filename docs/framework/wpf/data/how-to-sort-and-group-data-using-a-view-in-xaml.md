---
title: 如何：使用 XAML 排序和分組資料
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
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460122"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="83a11-102">如何：使用 XAML 排序和分組資料</span><span class="sxs-lookup"><span data-stu-id="83a11-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="83a11-103">這個範例示範如何在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中建立資料集合的視圖。</span><span class="sxs-lookup"><span data-stu-id="83a11-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="83a11-104">Views 允許群組、排序、篩選和目前專案的概念等功能。</span><span class="sxs-lookup"><span data-stu-id="83a11-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83a11-105">範例</span><span class="sxs-lookup"><span data-stu-id="83a11-105">Example</span></span>  
 <span data-ttu-id="83a11-106">在下列範例中，名為「*位置*」的靜態資源會定義為「*位置*」物件的集合，其中每個「*位置*」物件都是由「城市」名稱和「州」（city）組成。</span><span class="sxs-lookup"><span data-stu-id="83a11-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="83a11-107">前置詞*src*會對應至定義資料來源*位置*所在的命名空間。</span><span class="sxs-lookup"><span data-stu-id="83a11-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="83a11-108">首碼*scm*會對應到 `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` 和*dat*對應以 `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`。</span><span class="sxs-lookup"><span data-stu-id="83a11-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="83a11-109">下列範例會建立依城市名稱排序並依州/省分組之資料集合的視圖。</span><span class="sxs-lookup"><span data-stu-id="83a11-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="83a11-110">然後，此視圖可以是系結來源，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="83a11-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="83a11-111">若為系結至 <xref:System.Windows.Data.XmlDataProvider> 資源中定義的 XML 資料，請在 XML 名稱前面加上 @ 符號。</span><span class="sxs-lookup"><span data-stu-id="83a11-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="83a11-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="83a11-112">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="83a11-113">取得資料集合的預設檢視</span><span class="sxs-lookup"><span data-stu-id="83a11-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="83a11-114">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="83a11-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="83a11-115">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="83a11-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
