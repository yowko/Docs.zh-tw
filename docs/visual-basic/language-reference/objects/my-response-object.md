---
title: My.Response 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 53e8012e762c46e6efbd8e9d2191aa62d58aa42b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870038"
---
# <a name="myresponse-object"></a><span data-ttu-id="3e051-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="3e051-102">My.Response Object</span></span>

<span data-ttu-id="3e051-103">取得 <xref:System.Web.HttpResponse> 與相關聯的物件 <xref:System.Web.UI.Page> 。</span><span class="sxs-lookup"><span data-stu-id="3e051-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="3e051-104">此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3e051-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e051-105">備註</span><span class="sxs-lookup"><span data-stu-id="3e051-105">Remarks</span></span>  

 <span data-ttu-id="3e051-106">`My.Response`物件包含 <xref:System.Web.HttpResponse> 與頁面相關聯的目前物件。</span><span class="sxs-lookup"><span data-stu-id="3e051-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="3e051-107">`My.Response`物件僅適用于 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e051-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e051-108">範例</span><span class="sxs-lookup"><span data-stu-id="3e051-108">Example</span></span>  

 <span data-ttu-id="3e051-109">下列範例會從物件取得標頭集合 `My.Request` ，並使用 `My.Response` 物件將它寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="3e051-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3e051-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e051-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="3e051-111">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="3e051-111">My.Request Object</span></span>](my-request-object.md)
