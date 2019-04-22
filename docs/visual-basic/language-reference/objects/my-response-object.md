---
title: My.Response 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 2f72f493d99c1e0b0469150c041649486e5ed124
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818991"
---
# <a name="myresponse-object"></a><span data-ttu-id="f9eb2-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="f9eb2-102">My.Response Object</span></span>
<span data-ttu-id="f9eb2-103">取得<xref:System.Web.HttpResponse>相關聯的物件<xref:System.Web.UI.Page>。</span><span class="sxs-lookup"><span data-stu-id="f9eb2-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="f9eb2-104">此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f9eb2-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9eb2-105">備註</span><span class="sxs-lookup"><span data-stu-id="f9eb2-105">Remarks</span></span>  
 <span data-ttu-id="f9eb2-106">`My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="f9eb2-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="f9eb2-107">`My.Response`僅適用於物件[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9eb2-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9eb2-108">範例</span><span class="sxs-lookup"><span data-stu-id="f9eb2-108">Example</span></span>  
 <span data-ttu-id="f9eb2-109">下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="f9eb2-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f9eb2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9eb2-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="f9eb2-111">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="f9eb2-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
