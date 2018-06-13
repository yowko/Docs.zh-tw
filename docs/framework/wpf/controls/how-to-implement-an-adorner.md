---
title: 如何：實作裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: f5b0ed080a413546a3b985055858e209f9f347eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552961"
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="b3b8c-102">如何：實作裝飾項</span><span class="sxs-lookup"><span data-stu-id="b3b8c-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="b3b8c-103">此範例會顯示最少的裝飾項的實作。</span><span class="sxs-lookup"><span data-stu-id="b3b8c-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="b3b8c-104">實作者注意事項</span><span class="sxs-lookup"><span data-stu-id="b3b8c-104">Notes for Implementers</span></span>  
 <span data-ttu-id="b3b8c-105">請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。</span><span class="sxs-lookup"><span data-stu-id="b3b8c-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="b3b8c-106">實作轉譯行為的常見方式是覆寫<xref:System.Windows.UIElement.OnRender%2A>方法並使用一或多個<xref:System.Windows.Media.DrawingContext>物件來呈現裝飾項的視覺效果視 （如本範例所示）。</span><span class="sxs-lookup"><span data-stu-id="b3b8c-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3b8c-107">範例</span><span class="sxs-lookup"><span data-stu-id="b3b8c-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b3b8c-108">描述</span><span class="sxs-lookup"><span data-stu-id="b3b8c-108">Description</span></span>  
 <span data-ttu-id="b3b8c-109">藉由實作繼承自抽象類別建立的自訂裝飾項<xref:System.Windows.Documents.Adorner>類別。</span><span class="sxs-lookup"><span data-stu-id="b3b8c-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="b3b8c-110">範例裝飾項只 adorns 角落<xref:System.Windows.UIElement>使用圓形藉由覆寫<xref:System.Windows.UIElement.OnRender%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b3b8c-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b3b8c-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="b3b8c-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="b3b8c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3b8c-112">See Also</span></span>  
 [<span data-ttu-id="b3b8c-113">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="b3b8c-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
