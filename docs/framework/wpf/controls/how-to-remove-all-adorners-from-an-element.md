---
title: HOW TO：移除項目的所有裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 310b0249c215801b2634d51a1a1117bd7df83526
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680178"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="a1628-102">HOW TO：移除項目的所有裝飾項</span><span class="sxs-lookup"><span data-stu-id="a1628-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="a1628-103">此範例示範如何以程式設計方式移除所有裝飾指定<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="a1628-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1628-104">範例</span><span class="sxs-lookup"><span data-stu-id="a1628-104">Example</span></span>  
 <span data-ttu-id="a1628-105">此詳細的程式碼範例會移除所有裝飾項中所傳回的裝飾項的陣列<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。</span><span class="sxs-lookup"><span data-stu-id="a1628-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="a1628-106">此範例會擷取上的裝飾項<xref:System.Windows.UIElement>名為*myTextBox*。</span><span class="sxs-lookup"><span data-stu-id="a1628-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="a1628-107">呼叫中指定的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有任何裝飾項，`null`會傳回。</span><span class="sxs-lookup"><span data-stu-id="a1628-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="a1628-108">此程式碼明確檢查有 null 的陣列，最適合應用程式的 null 陣列應該在其中應該相當常見。</span><span class="sxs-lookup"><span data-stu-id="a1628-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="a1628-109">範例</span><span class="sxs-lookup"><span data-stu-id="a1628-109">Example</span></span>  
 <span data-ttu-id="a1628-110">此壓縮之程式碼範例是功能上相當於上面顯示的詳細資訊的範例。</span><span class="sxs-lookup"><span data-stu-id="a1628-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="a1628-111">此程式碼不會明確檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1628-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="a1628-112">此程式碼最適合用於應用程式，使用 null 陣列應該很少見。</span><span class="sxs-lookup"><span data-stu-id="a1628-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="a1628-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1628-113">See also</span></span>
- [<span data-ttu-id="a1628-114">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="a1628-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
