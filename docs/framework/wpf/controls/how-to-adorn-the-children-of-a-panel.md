---
title: 作法：裝飾 Panel 的子系
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 739ccaa0273e66c4650c35217a1156d64336dbbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923518"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="e8b90-102">HOW TO：裝飾 Panel 的子系</span><span class="sxs-lookup"><span data-stu-id="e8b90-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="e8b90-103">這個範例會示範如何以程式設計方式, 將裝飾項系結<xref:System.Windows.Controls.Panel>至指定之的子系。</span><span class="sxs-lookup"><span data-stu-id="e8b90-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b90-104">範例</span><span class="sxs-lookup"><span data-stu-id="e8b90-104">Example</span></span>  
 <span data-ttu-id="e8b90-105">若要將裝飾項<xref:System.Windows.Controls.Panel>系結至的子系, 請遵循下列步驟:</span><span class="sxs-lookup"><span data-stu-id="e8b90-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="e8b90-106">宣告新<xref:System.Windows.Documents.AdornerLayer>的物件, 並`static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>呼叫方法, 以尋找要裝飾其子系之專案的裝飾項層。</span><span class="sxs-lookup"><span data-stu-id="e8b90-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="e8b90-107">列舉父元素的子系, 並呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法, 將裝飾項系結至每個子專案。</span><span class="sxs-lookup"><span data-stu-id="e8b90-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="e8b90-108">下列範例會將 SimpleCircleAdorner (如上所示) 系結至<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*的子系。</span><span class="sxs-lookup"><span data-stu-id="e8b90-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
> <span data-ttu-id="e8b90-109">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。</span><span class="sxs-lookup"><span data-stu-id="e8b90-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b90-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8b90-110">See also</span></span>

- [<span data-ttu-id="e8b90-111">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="e8b90-111">Adorners Overview</span></span>](adorners-overview.md)
