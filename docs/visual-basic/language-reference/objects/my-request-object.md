---
title: My.Request 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: a9af211df358b8c87cc9735f05d18c191b49500e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716191"
---
# <a name="myrequest-object"></a><span data-ttu-id="63d01-102">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="63d01-102">My.Request Object</span></span>
<span data-ttu-id="63d01-103">取得所要求頁面的 <xref:System.Web.HttpRequest> 物件。</span><span class="sxs-lookup"><span data-stu-id="63d01-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63d01-104">備註</span><span class="sxs-lookup"><span data-stu-id="63d01-104">Remarks</span></span>  
 <span data-ttu-id="63d01-105">`My.Request` 物件包含目前 HTTP 要求的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="63d01-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="63d01-106">`My.Request` 物件僅適用於 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="63d01-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63d01-107">範例</span><span class="sxs-lookup"><span data-stu-id="63d01-107">Example</span></span>  
 <span data-ttu-id="63d01-108">下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="63d01-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="63d01-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63d01-109">See also</span></span>
- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="63d01-110">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="63d01-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
