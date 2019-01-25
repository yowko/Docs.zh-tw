---
title: HOW TO：取得頁面函式的傳回值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- functions [WPF], getting return values of
- page functions [WPF], getting return values of
- return values of page functions [WPF]
- getting [WPF], return values of page functions
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
ms.openlocfilehash: 8ac1b59330790432ac29edd63a37db44283ba542
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724209"
---
# <a name="how-to-get-the-return-value-of-a-page-function"></a><span data-ttu-id="077af-102">HOW TO：取得頁面函式的傳回值</span><span class="sxs-lookup"><span data-stu-id="077af-102">How to: Get the Return Value of a Page Function</span></span>
<span data-ttu-id="077af-103">此範例示範如何取得頁面函式傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="077af-103">This example shows how to get the result that is returned by a page function.</span></span>  
  
## <a name="example"></a><span data-ttu-id="077af-104">範例</span><span class="sxs-lookup"><span data-stu-id="077af-104">Example</span></span>  
 <span data-ttu-id="077af-105">若要取得頁面函式傳回的結果，您需要處理<xref:System.Windows.Navigation.PageFunction%601.Return>您要呼叫之頁面函式。</span><span class="sxs-lookup"><span data-stu-id="077af-105">To get the result that is returned from a page function, you need to handle <xref:System.Windows.Navigation.PageFunction%601.Return> of the page function you are calling.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="077af-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="077af-106">See also</span></span>
- <xref:System.Windows.Navigation.PageFunction%601>
