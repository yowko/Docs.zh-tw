---
title: Request 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: da17872acb839cdcdfa7f80c3f58f26dc25d0ab5
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567469"
---
# <a name="myrequest-object"></a>My.Request 物件
取得所要求頁面的 <xref:System.Web.HttpRequest> 物件。  
  
## <a name="remarks"></a>備註  
 `My.Request` 物件包含目前 HTTP 要求的相關資訊。  
  
 `My.Request` 物件僅適用於 ASP.NET 應用程式。  
  
## <a name="example"></a>範例  
 下列範例會從`My.Request`物件取得標頭集合, 並`My.Response`使用物件將其寫入至 ASP.NET 網頁。  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Web.HttpRequest>
- [My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)
