---
title: 如何：從項目移除裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: a3e1b08a9ec5e2cd60c063ced5e5f0d5874f8184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551839"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="5c265-102">如何：從項目移除裝飾項</span><span class="sxs-lookup"><span data-stu-id="5c265-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="5c265-103">這個範例示範如何以程式設計方式移除特定的裝飾項指定<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="5c265-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c265-104">範例</span><span class="sxs-lookup"><span data-stu-id="5c265-104">Example</span></span>  
 <span data-ttu-id="5c265-105">這個冗長的程式碼範例的提示所傳回陣列中移除第一個裝飾項<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。</span><span class="sxs-lookup"><span data-stu-id="5c265-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="5c265-106">此範例中會發生要擷取的裝飾項在<xref:System.Windows.UIElement>名為*myTextBox*。</span><span class="sxs-lookup"><span data-stu-id="5c265-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="5c265-107">如果指定的呼叫中的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有無裝飾項，`null`傳回。</span><span class="sxs-lookup"><span data-stu-id="5c265-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="5c265-108">此程式碼明確檢查 null 的陣列，以及最適合應用程式其中 null 陣列必須是相對常見。</span><span class="sxs-lookup"><span data-stu-id="5c265-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="5c265-109">範例</span><span class="sxs-lookup"><span data-stu-id="5c265-109">Example</span></span>  
 <span data-ttu-id="5c265-110">此壓縮的程式碼範例是功能上相當於上面顯示的詳細資訊的範例。</span><span class="sxs-lookup"><span data-stu-id="5c265-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="5c265-111">此程式碼不會明確地檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c265-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="5c265-112">此程式碼最適合用於應用程式的 null 陣列應該很少見。</span><span class="sxs-lookup"><span data-stu-id="5c265-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="5c265-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c265-113">See Also</span></span>  
 [<span data-ttu-id="5c265-114">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="5c265-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
