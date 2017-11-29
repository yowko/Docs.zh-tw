---
title: "如何：移除項目的所有裝飾項"
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
helpviewer_keywords: adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9b69b9150e8d2c2938c53fcd47e72b7fcb6d238
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="e4010-102">如何：移除項目的所有裝飾項</span><span class="sxs-lookup"><span data-stu-id="e4010-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="e4010-103">這個範例示範如何以程式設計方式移除所有裝飾指定<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="e4010-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4010-104">範例</span><span class="sxs-lookup"><span data-stu-id="e4010-104">Example</span></span>  
 <span data-ttu-id="e4010-105">這個冗長的程式碼範例會移除所有裝飾項的提示所傳回陣列中<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。</span><span class="sxs-lookup"><span data-stu-id="e4010-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="e4010-106">此範例中會發生要擷取的裝飾項在<xref:System.Windows.UIElement>名為*myTextBox*。</span><span class="sxs-lookup"><span data-stu-id="e4010-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="e4010-107">如果指定的呼叫中的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有無裝飾項，`null`傳回。</span><span class="sxs-lookup"><span data-stu-id="e4010-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="e4010-108">此程式碼明確檢查 null 的陣列，以及最適合應用程式其中 null 陣列必須是相對常見。</span><span class="sxs-lookup"><span data-stu-id="e4010-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="e4010-109">範例</span><span class="sxs-lookup"><span data-stu-id="e4010-109">Example</span></span>  
 <span data-ttu-id="e4010-110">此壓縮的程式碼範例是功能上相當於上面顯示的詳細資訊的範例。</span><span class="sxs-lookup"><span data-stu-id="e4010-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="e4010-111">此程式碼不會明確地檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e4010-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="e4010-112">此程式碼最適合用於應用程式的 null 陣列應該很少見。</span><span class="sxs-lookup"><span data-stu-id="e4010-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="e4010-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4010-113">See Also</span></span>  
 [<span data-ttu-id="e4010-114">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="e4010-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
