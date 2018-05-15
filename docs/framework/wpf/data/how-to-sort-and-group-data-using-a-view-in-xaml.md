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
ms.openlocfilehash: 80529420bcc5fdca473313e164b3d096732953f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="afc09-102">如何：使用 XAML 排序和分組資料</span><span class="sxs-lookup"><span data-stu-id="afc09-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="afc09-103">這個範例示範如何建立資料集合中的檢視[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="afc09-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="afc09-104">檢視可讓分組、 排序、 篩選的功能和目前項目的概念。</span><span class="sxs-lookup"><span data-stu-id="afc09-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afc09-105">範例</span><span class="sxs-lookup"><span data-stu-id="afc09-105">Example</span></span>  
 <span data-ttu-id="afc09-106">在下列範例中，靜態資源名為*放置*做為集合定義*位置*中每個物件，*位置*物件組成的縣 （市） 名稱和狀態。</span><span class="sxs-lookup"><span data-stu-id="afc09-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="afc09-107">前置詞*src*對應至命名空間所在的資料來源*數位*定義。</span><span class="sxs-lookup"><span data-stu-id="afc09-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="afc09-108">前置詞*scm*對應至`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`和*dat*對應至`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`。</span><span class="sxs-lookup"><span data-stu-id="afc09-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="afc09-109">下列範例會建立一個檢視是依城市名稱排序，並依狀態分組的資料集合。</span><span class="sxs-lookup"><span data-stu-id="afc09-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="afc09-110">檢視可繫結來源，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="afc09-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="afc09-111">對於 XML 資料中定義的繫結<xref:System.Windows.Data.XmlDataProvider>資源 XML 名前加上 @ 符號。</span><span class="sxs-lookup"><span data-stu-id="afc09-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="afc09-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afc09-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="afc09-113">取得資料集合的預設檢視</span><span class="sxs-lookup"><span data-stu-id="afc09-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="afc09-114">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="afc09-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="afc09-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="afc09-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
