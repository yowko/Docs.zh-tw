---
title: My.Response 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372452"
---
# <a name="myresponse-object"></a><span data-ttu-id="b084c-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="b084c-102">My.Response Object</span></span>
<span data-ttu-id="b084c-103">取得 <xref:System.Web.HttpResponse> 與相關聯的物件 <xref:System.Web.UI.Page> 。</span><span class="sxs-lookup"><span data-stu-id="b084c-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="b084c-104">此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b084c-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b084c-105">備註</span><span class="sxs-lookup"><span data-stu-id="b084c-105">Remarks</span></span>  
 <span data-ttu-id="b084c-106">`My.Response`物件包含 <xref:System.Web.HttpResponse> 與頁面相關聯的目前物件。</span><span class="sxs-lookup"><span data-stu-id="b084c-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="b084c-107">`My.Response`物件僅適用于 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b084c-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b084c-108">範例</span><span class="sxs-lookup"><span data-stu-id="b084c-108">Example</span></span>  
 <span data-ttu-id="b084c-109">下列範例會從物件取得標頭集合 `My.Request` ，並使用 `My.Response` 物件將其寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="b084c-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b084c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b084c-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="b084c-111">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="b084c-111">My.Request Object</span></span>](my-request-object.md)
