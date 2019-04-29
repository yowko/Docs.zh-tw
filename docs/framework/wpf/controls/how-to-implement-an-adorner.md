---
title: HOW TO：實作 Adorner
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: da318fee42b4628351217774de2a2225cfb21ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770977"
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="fc1bd-102">HOW TO：實作 Adorner</span><span class="sxs-lookup"><span data-stu-id="fc1bd-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="fc1bd-103">此範例中顯示的最小的裝飾項實作。</span><span class="sxs-lookup"><span data-stu-id="fc1bd-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="fc1bd-104">實作者的附註</span><span class="sxs-lookup"><span data-stu-id="fc1bd-104">Notes for Implementers</span></span>  
 <span data-ttu-id="fc1bd-105">請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。</span><span class="sxs-lookup"><span data-stu-id="fc1bd-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="fc1bd-106">實作轉譯行為的常見方式是覆寫<xref:System.Windows.UIElement.OnRender%2A>方法，並使用一或多個<xref:System.Windows.Media.DrawingContext>轉譯裝飾項的視覺效果所需 （如本範例所示） 的物件。</span><span class="sxs-lookup"><span data-stu-id="fc1bd-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc1bd-107">範例</span><span class="sxs-lookup"><span data-stu-id="fc1bd-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fc1bd-108">描述</span><span class="sxs-lookup"><span data-stu-id="fc1bd-108">Description</span></span>  
 <span data-ttu-id="fc1bd-109">藉由實作繼承自抽象類別來建立自訂裝飾項<xref:System.Windows.Documents.Adorner>類別。</span><span class="sxs-lookup"><span data-stu-id="fc1bd-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="fc1bd-110">裝飾項範例只會裝飾的邊角<xref:System.Windows.UIElement>具有藉由覆寫的圓圈<xref:System.Windows.UIElement.OnRender%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="fc1bd-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fc1bd-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="fc1bd-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="fc1bd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc1bd-112">See also</span></span>

- [<span data-ttu-id="fc1bd-113">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="fc1bd-113">Adorners Overview</span></span>](adorners-overview.md)
