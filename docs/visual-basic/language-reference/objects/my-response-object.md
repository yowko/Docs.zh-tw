---
title: My.Response 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 5677108ac31733577915e15972386d8de5ccba49
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203346"
---
# <a name="myresponse-object"></a><span data-ttu-id="51e23-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="51e23-102">My.Response Object</span></span>
<span data-ttu-id="51e23-103">取得<xref:System.Web.HttpResponse>相關聯的物件<xref:System.Web.UI.Page>。</span><span class="sxs-lookup"><span data-stu-id="51e23-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="51e23-104">此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="51e23-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51e23-105">備註</span><span class="sxs-lookup"><span data-stu-id="51e23-105">Remarks</span></span>  
 <span data-ttu-id="51e23-106">`My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="51e23-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="51e23-107">`My.Response`僅適用於物件[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="51e23-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51e23-108">範例</span><span class="sxs-lookup"><span data-stu-id="51e23-108">Example</span></span>  
 <span data-ttu-id="51e23-109">下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="51e23-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="51e23-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51e23-110">See also</span></span>
- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="51e23-111">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="51e23-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
