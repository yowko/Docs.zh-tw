---
title: My.Response 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0a907d74112586e7b88c5a0a6f40080455454d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="myresponse-object"></a>My.Response 物件
取得<xref:System.Web.HttpResponse>物件相關聯<xref:System.Web.UI.Page>。 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。  
  
## <a name="remarks"></a>備註  
 `My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面相關聯的物件。  
  
 `My.Response`物件只適用於[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。  
  
## <a name="example"></a>範例  
 下列範例會取得標頭集合中的從`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 頁面。  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Web.HttpResponse>  
 [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
