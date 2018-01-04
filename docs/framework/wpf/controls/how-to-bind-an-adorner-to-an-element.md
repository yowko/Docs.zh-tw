---
title: "如何：將裝飾項繫結至項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3c657cde9da19f8ebc6b6d4d05077ed027781b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="de2f9-102">如何：將裝飾項繫結至項目</span><span class="sxs-lookup"><span data-stu-id="de2f9-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="de2f9-103">這個範例示範如何以程式設計方式將裝飾項繫結至指定<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="de2f9-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de2f9-104">範例</span><span class="sxs-lookup"><span data-stu-id="de2f9-104">Example</span></span>  
 <span data-ttu-id="de2f9-105">若要將裝飾項繫結至特定<xref:System.Windows.UIElement>，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="de2f9-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="de2f9-106">呼叫`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>取得<xref:System.Windows.Documents.AdornerLayer>物件<xref:System.Windows.UIElement>至會裝飾。</span><span class="sxs-lookup"><span data-stu-id="de2f9-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="de2f9-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>開始於指定的視覺化樹狀結構會進入**UIElement**，並傳回它發現的第一個裝飾項層。</span><span class="sxs-lookup"><span data-stu-id="de2f9-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="de2f9-108">(如果找不到任何裝飾項圖層，方法會傳回 null。)</span><span class="sxs-lookup"><span data-stu-id="de2f9-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="de2f9-109">呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至目標**UIElement**。</span><span class="sxs-lookup"><span data-stu-id="de2f9-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="de2f9-110">下列範例會將繫結 （如上所示） 以 SimpleCircleAdorner<xref:System.Windows.Controls.TextBox>名為*myTextBox*。</span><span class="sxs-lookup"><span data-stu-id="de2f9-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="de2f9-111">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。</span><span class="sxs-lookup"><span data-stu-id="de2f9-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de2f9-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="de2f9-112">See Also</span></span>  
 [<span data-ttu-id="de2f9-113">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="de2f9-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
