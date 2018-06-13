---
title: My.Request 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 88c3a9a01b50a97b556fa94026df391248bdf912
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595884"
---
# <a name="myrequest-object"></a><span data-ttu-id="4844b-102">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="4844b-102">My.Request Object</span></span>
<span data-ttu-id="4844b-103">取得所要求頁面的 <xref:System.Web.HttpRequest> 物件。</span><span class="sxs-lookup"><span data-stu-id="4844b-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4844b-104">備註</span><span class="sxs-lookup"><span data-stu-id="4844b-104">Remarks</span></span>  
 <span data-ttu-id="4844b-105">`My.Request` 物件包含目前 HTTP 要求的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4844b-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="4844b-106">`My.Request` 物件僅適用於 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4844b-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4844b-107">範例</span><span class="sxs-lookup"><span data-stu-id="4844b-107">Example</span></span>  
 <span data-ttu-id="4844b-108">下列範例會取得標頭集合中的從`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 頁面。</span><span class="sxs-lookup"><span data-stu-id="4844b-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="4844b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4844b-109">See Also</span></span>  
 <xref:System.Web.HttpRequest>  
 [<span data-ttu-id="4844b-110">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="4844b-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
