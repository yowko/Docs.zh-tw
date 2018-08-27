---
title: My.Request 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: f2c43afb723944293907d0efbb4cf3cc66a40e1e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932546"
---
# <a name="myrequest-object"></a>My.Request 物件
取得所要求頁面的 <xref:System.Web.HttpRequest> 物件。  
  
## <a name="remarks"></a>備註  
 `My.Request` 物件包含目前 HTTP 要求的相關資訊。  
  
 `My.Request` 物件僅適用於 ASP.NET 應用程式。  
  
## <a name="example"></a>範例  
 下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 網頁。  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Web.HttpRequest>  
 [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)
