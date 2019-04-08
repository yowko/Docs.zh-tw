---
title: HOW TO：裝飾 Panel 的子系
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: e96e1772794a1594d97e1a0109d944d23515468d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100882"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="7bd81-102">HOW TO：裝飾 Panel 的子系</span><span class="sxs-lookup"><span data-stu-id="7bd81-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="7bd81-103">此範例示範如何以程式設計方式將裝飾項繫結至指定的子系<xref:System.Windows.Controls.Panel>。</span><span class="sxs-lookup"><span data-stu-id="7bd81-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bd81-104">範例</span><span class="sxs-lookup"><span data-stu-id="7bd81-104">Example</span></span>  
 <span data-ttu-id="7bd81-105">裝飾項繫結的項目子系<xref:System.Windows.Controls.Panel>，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7bd81-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7bd81-106">宣告新<xref:System.Windows.Documents.AdornerLayer>物件，然後呼叫`static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>方法來尋找要裝飾其子系的項目中的裝飾項層。</span><span class="sxs-lookup"><span data-stu-id="7bd81-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="7bd81-107">列舉父項目並呼叫的子系<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法的裝飾項繫結至每個子項目。</span><span class="sxs-lookup"><span data-stu-id="7bd81-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="7bd81-108">下列範例會將 SimpleCircleAdorner （如上所示） 的項目子系繫結<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*。</span><span class="sxs-lookup"><span data-stu-id="7bd81-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="7bd81-109">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。</span><span class="sxs-lookup"><span data-stu-id="7bd81-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd81-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bd81-110">See also</span></span>

- [<span data-ttu-id="7bd81-111">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="7bd81-111">Adorners Overview</span></span>](adorners-overview.md)
