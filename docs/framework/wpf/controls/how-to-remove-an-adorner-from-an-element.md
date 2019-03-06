---
title: HOW TO：從項目移除裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 0c74fe9ed1e7190ce4ff26a7dbae1413f950ba7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374072"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="d7a96-102">HOW TO：從項目移除裝飾項</span><span class="sxs-lookup"><span data-stu-id="d7a96-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="d7a96-103">此範例示範如何以程式設計方式從指定中移除特定的裝飾項<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="d7a96-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7a96-104">範例</span><span class="sxs-lookup"><span data-stu-id="d7a96-104">Example</span></span>  
 <span data-ttu-id="d7a96-105">此詳細的程式碼範例所傳回的裝飾項的陣列中移除第一個裝飾項<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。</span><span class="sxs-lookup"><span data-stu-id="d7a96-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="d7a96-106">此範例會擷取上的裝飾項<xref:System.Windows.UIElement>名為*myTextBox*。</span><span class="sxs-lookup"><span data-stu-id="d7a96-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="d7a96-107">呼叫中指定的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有任何裝飾項，`null`會傳回。</span><span class="sxs-lookup"><span data-stu-id="d7a96-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="d7a96-108">此程式碼明確檢查有 null 的陣列，最適合應用程式的 null 陣列應該在其中應該相當常見。</span><span class="sxs-lookup"><span data-stu-id="d7a96-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="d7a96-109">範例</span><span class="sxs-lookup"><span data-stu-id="d7a96-109">Example</span></span>  
 <span data-ttu-id="d7a96-110">此壓縮之程式碼範例是功能上相當於上面顯示的詳細資訊的範例。</span><span class="sxs-lookup"><span data-stu-id="d7a96-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="d7a96-111">此程式碼不會明確檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d7a96-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="d7a96-112">此程式碼最適合用於應用程式，使用 null 陣列應該很少見。</span><span class="sxs-lookup"><span data-stu-id="d7a96-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="d7a96-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7a96-113">See also</span></span>
- [<span data-ttu-id="d7a96-114">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="d7a96-114">Adorners Overview</span></span>](adorners-overview.md)
