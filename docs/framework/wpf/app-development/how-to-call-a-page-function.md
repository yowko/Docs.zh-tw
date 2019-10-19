---
title: 如何：呼叫頁面函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: f170977860a73d339f2d83bc43992e6e2bc4053f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582040"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="6e833-102">如何：呼叫頁面函式</span><span class="sxs-lookup"><span data-stu-id="6e833-102">How to: Call a Page Function</span></span>
<span data-ttu-id="6e833-103">這個範例示範如何從 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 頁面呼叫頁面函式。</span><span class="sxs-lookup"><span data-stu-id="6e833-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e833-104">範例</span><span class="sxs-lookup"><span data-stu-id="6e833-104">Example</span></span>  
 <span data-ttu-id="6e833-105">您可以使用統一資源識別元（URI）導覽至頁面函式，就像流覽至頁面時一樣。</span><span class="sxs-lookup"><span data-stu-id="6e833-105">You can navigate to a page function using a uniform resource identifier (URI), just as you can when you navigate to a page.</span></span> <span data-ttu-id="6e833-106">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="6e833-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="6e833-107">如果您必須將資料傳遞給頁面函式，您可以建立其執行個體，然後藉由設定屬性來傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="6e833-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="6e833-108">或者，如下列範例所示，您可以使用非無參數的函式來傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="6e833-108">Or, as the following example shows, you can pass the data using a non-parameterless constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="6e833-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e833-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
