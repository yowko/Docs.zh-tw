---
title: My.Response 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: d5f49529a2593093a234babc22f64b591ea3cc61
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071630"
---
# <a name="myresponse-object"></a><span data-ttu-id="05dfd-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="05dfd-102">My.Response Object</span></span>
<span data-ttu-id="05dfd-103">取得<xref:System.Web.HttpResponse>相關聯的物件<xref:System.Web.UI.Page>。</span><span class="sxs-lookup"><span data-stu-id="05dfd-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="05dfd-104">此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="05dfd-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05dfd-105">備註</span><span class="sxs-lookup"><span data-stu-id="05dfd-105">Remarks</span></span>  
 <span data-ttu-id="05dfd-106">`My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="05dfd-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="05dfd-107">`My.Response`僅適用於物件[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="05dfd-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05dfd-108">範例</span><span class="sxs-lookup"><span data-stu-id="05dfd-108">Example</span></span>  
 <span data-ttu-id="05dfd-109">下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="05dfd-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="05dfd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05dfd-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="05dfd-111">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="05dfd-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
