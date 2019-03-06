---
title: HOW TO：呼叫頁面函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: 288edec51a690be844aaa913c368496648a7811b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375164"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="452d4-102">HOW TO：呼叫頁面函式</span><span class="sxs-lookup"><span data-stu-id="452d4-102">How to: Call a Page Function</span></span>
<span data-ttu-id="452d4-103">此範例示範如何呼叫頁面函式從[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="452d4-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="452d4-104">範例</span><span class="sxs-lookup"><span data-stu-id="452d4-104">Example</span></span>  
 <span data-ttu-id="452d4-105">您可以巡覽至頁面函式使用[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，就像您可能會在您瀏覽的頁面時。</span><span class="sxs-lookup"><span data-stu-id="452d4-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="452d4-106">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="452d4-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="452d4-107">如果您必須將資料傳遞給頁面函式，您可以建立其執行個體，然後藉由設定屬性來傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="452d4-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="452d4-108">或者，如下列範例所示，您也可以使用非預設建構函式來傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="452d4-108">Or, as the following example shows, you can pass the data using a non-default constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="452d4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="452d4-109">See also</span></span>
- <xref:System.Windows.Navigation.PageFunction%601>
