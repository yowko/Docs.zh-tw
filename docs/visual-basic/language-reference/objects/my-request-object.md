---
title: My.Request 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 38f510e2a3958761b902f37760069aa8d595ea8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372423"
---
# <a name="myrequest-object"></a><span data-ttu-id="4ac0a-102">My.Request 物件</span><span class="sxs-lookup"><span data-stu-id="4ac0a-102">My.Request Object</span></span>
<span data-ttu-id="4ac0a-103">取得所要求頁面的 <xref:System.Web.HttpRequest> 物件。</span><span class="sxs-lookup"><span data-stu-id="4ac0a-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ac0a-104">備註</span><span class="sxs-lookup"><span data-stu-id="4ac0a-104">Remarks</span></span>  
 <span data-ttu-id="4ac0a-105">`My.Request` 物件包含目前 HTTP 要求的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4ac0a-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="4ac0a-106">`My.Request` 物件僅適用於 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4ac0a-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac0a-107">範例</span><span class="sxs-lookup"><span data-stu-id="4ac0a-107">Example</span></span>  
 <span data-ttu-id="4ac0a-108">下列範例會從物件取得標頭集合 `My.Request` ，並使用 `My.Response` 物件將其寫入至 ASP.NET 網頁。</span><span class="sxs-lookup"><span data-stu-id="4ac0a-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4ac0a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ac0a-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="4ac0a-110">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="4ac0a-110">My.Response Object</span></span>](my-response-object.md)
