---
title: "My.Response 物件 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
dev_langs:
- VB
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b9b34c9df31536f6d553cda2e26677a2645768c2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="myresponse-object"></a><span data-ttu-id="62525-102">My.Response 物件</span><span class="sxs-lookup"><span data-stu-id="62525-102">My.Response Object</span></span>
<span data-ttu-id="62525-103">取得<xref:System.Web.HttpResponse>物件相關聯<xref:System.Web.UI.Page>.</xref:System.Web.UI.Page> </xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="62525-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="62525-104">此物件可讓您傳送給用戶端的 HTTP 回應資料，並包含有關該回應的資訊。</span><span class="sxs-lookup"><span data-stu-id="62525-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62525-105">備註</span><span class="sxs-lookup"><span data-stu-id="62525-105">Remarks</span></span>  
 <span data-ttu-id="62525-106">`My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面相關聯的物件。</xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="62525-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="62525-107">`My.Response`物件只適用於[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="62525-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62525-108">範例</span><span class="sxs-lookup"><span data-stu-id="62525-108">Example</span></span>  
 <span data-ttu-id="62525-109">下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`撰寫 ASP.NET 網頁上的物件。</span><span class="sxs-lookup"><span data-stu-id="62525-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 <span data-ttu-id="62525-110">[!code-vb[VbVbalrMyWeb #&1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]</span><span class="sxs-lookup"><span data-stu-id="62525-110">[!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62525-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62525-111">See Also</span></span>  
 <span data-ttu-id="62525-112"><xref:System.Web.HttpResponse></xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="62525-112"><xref:System.Web.HttpResponse></span></span>   
<span data-ttu-id="62525-113"> [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)</span><span class="sxs-lookup"><span data-stu-id="62525-113"> [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)</span></span>
