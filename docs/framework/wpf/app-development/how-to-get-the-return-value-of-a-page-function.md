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
ms.openlocfilehash: fd54a5059d028f9fc6624d1e2d03b209140b481c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365131"
---
# <a name="how-to-get-the-return-value-of-a-page-function"></a><span data-ttu-id="2ae0b-102">HOW TO：取得頁面函式的傳回值</span><span class="sxs-lookup"><span data-stu-id="2ae0b-102">How to: Get the Return Value of a Page Function</span></span>
<span data-ttu-id="2ae0b-103">此範例示範如何取得頁面函式傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="2ae0b-103">This example shows how to get the result that is returned by a page function.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ae0b-104">範例</span><span class="sxs-lookup"><span data-stu-id="2ae0b-104">Example</span></span>  
 <span data-ttu-id="2ae0b-105">若要取得頁面函式傳回的結果，您需要處理<xref:System.Windows.Navigation.PageFunction%601.Return>您要呼叫之頁面函式。</span><span class="sxs-lookup"><span data-stu-id="2ae0b-105">To get the result that is returned from a page function, you need to handle <xref:System.Windows.Navigation.PageFunction%601.Return> of the page function you are calling.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="2ae0b-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ae0b-106">See also</span></span>
- <xref:System.Windows.Navigation.PageFunction%601>
