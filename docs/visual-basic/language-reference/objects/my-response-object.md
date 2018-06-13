---
title: My.Response 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0a907d74112586e7b88c5a0a6f40080455454d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597519"
---
# <a name="myresponse-object"></a><span data-ttu-id="e4ab0-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="e4ab0-102">My.Response Object</span></span>
<span data-ttu-id="e4ab0-103">取得<xref:System.Web.HttpResponse>物件相關聯<xref:System.Web.UI.Page>。</span><span class="sxs-lookup"><span data-stu-id="e4ab0-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="e4ab0-104">此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4ab0-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4ab0-105">備註</span><span class="sxs-lookup"><span data-stu-id="e4ab0-105">Remarks</span></span>  
 <span data-ttu-id="e4ab0-106">`My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="e4ab0-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="e4ab0-107">`My.Response`物件只適用於[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4ab0-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4ab0-108">範例</span><span class="sxs-lookup"><span data-stu-id="e4ab0-108">Example</span></span>  
 <span data-ttu-id="e4ab0-109">下列範例會取得標頭集合中的從`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 頁面。</span><span class="sxs-lookup"><span data-stu-id="e4ab0-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="e4ab0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4ab0-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="e4ab0-111">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="e4ab0-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
