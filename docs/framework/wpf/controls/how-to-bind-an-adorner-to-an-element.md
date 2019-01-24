---
title: HOW TO：將裝飾項繫結至項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: 91dd047e65af8791f8e558a9a3b622ef05e2cb77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606318"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="6f28e-102">HOW TO：將裝飾項繫結至項目</span><span class="sxs-lookup"><span data-stu-id="6f28e-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="6f28e-103">此範例示範如何以程式設計方式將裝飾項繫結至指定<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="6f28e-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f28e-104">範例</span><span class="sxs-lookup"><span data-stu-id="6f28e-104">Example</span></span>  
 <span data-ttu-id="6f28e-105">裝飾項繫結至特定<xref:System.Windows.UIElement>，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6f28e-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6f28e-106">呼叫`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>若要取得<xref:System.Windows.Documents.AdornerLayer>物件<xref:System.Windows.UIElement>裝飾。</span><span class="sxs-lookup"><span data-stu-id="6f28e-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="6f28e-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 始於指定的視覺化樹狀結構中向上**UIElement**，並傳回第一個找到的裝飾項圖層。</span><span class="sxs-lookup"><span data-stu-id="6f28e-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="6f28e-108">(如果找不到任何裝飾項圖層，方法會傳回 null。)</span><span class="sxs-lookup"><span data-stu-id="6f28e-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="6f28e-109">呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>裝飾項繫結至目標方法**UIElement**。</span><span class="sxs-lookup"><span data-stu-id="6f28e-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="6f28e-110">下列範例會將 SimpleCircleAdorner （如上所示） 來繫結<xref:System.Windows.Controls.TextBox>名為*myTextBox*。</span><span class="sxs-lookup"><span data-stu-id="6f28e-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="6f28e-111">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。</span><span class="sxs-lookup"><span data-stu-id="6f28e-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f28e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f28e-112">See also</span></span>
- [<span data-ttu-id="6f28e-113">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="6f28e-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
