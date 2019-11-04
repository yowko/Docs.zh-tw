---
title: 如何：使用應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460264"
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="e59de-102">如何：使用應用程式資源</span><span class="sxs-lookup"><span data-stu-id="e59de-102">How to: Use Application Resources</span></span>
<span data-ttu-id="e59de-103">這個範例示範如何使用應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="e59de-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e59de-104">範例</span><span class="sxs-lookup"><span data-stu-id="e59de-104">Example</span></span>  
 <span data-ttu-id="e59de-105">下列範例顯示應用程式定義檔案。</span><span class="sxs-lookup"><span data-stu-id="e59de-105">The following example shows an application definition file.</span></span> <span data-ttu-id="e59de-106">應用程式定義檔會定義資源區段（<xref:System.Windows.Application.Resources%2A> 屬性的值）。</span><span class="sxs-lookup"><span data-stu-id="e59de-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="e59de-107">如果資源是定義為應用程式層級，則應用程式當中的其他所有頁面均可存取這些資源。</span><span class="sxs-lookup"><span data-stu-id="e59de-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="e59de-108">在此情況下，這類資源是宣告的樣式。</span><span class="sxs-lookup"><span data-stu-id="e59de-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="e59de-109">因為包含控制項範本的完整樣式可能會很冗長，所以這個範例會省略在樣式的 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 屬性 setter 中定義的控制項範本。</span><span class="sxs-lookup"><span data-stu-id="e59de-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="e59de-110">下列範例顯示的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會參考上一個範例所定義的應用層級資源。</span><span class="sxs-lookup"><span data-stu-id="e59de-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="e59de-111">藉由使用[StaticResource 標記延伸](staticresource-markup-extension.md)來參考資源，以指定所要求資源的唯一資源金鑰。</span><span class="sxs-lookup"><span data-stu-id="e59de-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="e59de-112">目前的頁面找不到任何含有 "GelButton" 索引鍵的資源，因此，所要求資源的資源查閱範圍會繼續延伸到目前頁面以外和已定義的應用程式層級資源當中。</span><span class="sxs-lookup"><span data-stu-id="e59de-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="e59de-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e59de-113">See also</span></span>

- [<span data-ttu-id="e59de-114">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="e59de-114">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="e59de-115">應用程式管理概觀</span><span class="sxs-lookup"><span data-stu-id="e59de-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="e59de-116">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="e59de-116">How-to Topics</span></span>](resources-how-to-topics.md)
