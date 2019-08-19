---
title: 我的 Response 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567447"
---
# <a name="myresponse-object"></a>My.Response 物件
取得與相關聯的<xref:System.Web.HttpResponse>物件。 <xref:System.Web.UI.Page> 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。  
  
## <a name="remarks"></a>備註  
 物件包含與頁面相關<xref:System.Web.HttpResponse>聯的目前物件。 `My.Response`  
  
 `My.Response`物件僅適用于 ASP.NET 應用程式。  
  
## <a name="example"></a>範例  
 下列範例會從`My.Request`物件取得標頭集合, 並`My.Response`使用物件將其寫入至 ASP.NET 網頁。  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Web.HttpResponse>
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
