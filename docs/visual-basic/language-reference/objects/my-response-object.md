---
title: 我的 Response 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567447"
---
# <a name="myresponse-object"></a><span data-ttu-id="955a6-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="955a6-102">My.Response Object</span></span>
<span data-ttu-id="955a6-103">取得與相關聯的<xref:System.Web.HttpResponse>物件。 <xref:System.Web.UI.Page></span><span class="sxs-lookup"><span data-stu-id="955a6-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="955a6-104">此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="955a6-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="955a6-105">備註</span><span class="sxs-lookup"><span data-stu-id="955a6-105">Remarks</span></span>  
 <span data-ttu-id="955a6-106">物件包含與頁面相關<xref:System.Web.HttpResponse>聯的目前物件。 `My.Response`</span><span class="sxs-lookup"><span data-stu-id="955a6-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="955a6-107">`My.Response`物件僅適用于 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="955a6-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="955a6-108">範例</span><span class="sxs-lookup"><span data-stu-id="955a6-108">Example</span></span>  
 <span data-ttu-id="955a6-109">下列範例會從`My.Request`物件取得標頭集合, 並`My.Response`使用物件將其寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="955a6-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="955a6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="955a6-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="955a6-111">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="955a6-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
