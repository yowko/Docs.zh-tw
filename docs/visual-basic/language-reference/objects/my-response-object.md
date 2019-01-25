---
title: My.Response 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: c133e46b1adff0c100d49c4bfe5e17db4314a0bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738809"
---
# <a name="myresponse-object"></a>My.Response 物件
取得<xref:System.Web.HttpResponse>相關聯的物件<xref:System.Web.UI.Page>。 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。  
  
## <a name="remarks"></a>備註  
 `My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面關聯的物件。  
  
 `My.Response`僅適用於物件[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。  
  
## <a name="example"></a>範例  
 下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 網頁。  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Web.HttpResponse>
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
