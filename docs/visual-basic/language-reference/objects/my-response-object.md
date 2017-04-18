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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e2ae9a659bb7575023dfa1847c9d405d0f7d6ac3
ms.lasthandoff: 03/13/2017

---
# <a name="myresponse-object"></a>My.Response 物件
取得<xref:System.Web.HttpResponse>物件相關聯<xref:System.Web.UI.Page>.</xref:System.Web.UI.Page> </xref:System.Web.HttpResponse> 此物件可讓您傳送給用戶端的 HTTP 回應資料，並包含有關該回應的資訊。  
  
## <a name="remarks"></a>備註  
 `My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面相關聯的物件。</xref:System.Web.HttpResponse>  
  
 `My.Response`物件只適用於[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]應用程式。  
  
## <a name="example"></a>範例  
 下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`撰寫 ASP.NET 網頁上的物件。  
  
 [!code-vb[VbVbalrMyWeb #&1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Web.HttpResponse></xref:System.Web.HttpResponse>   
 [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
