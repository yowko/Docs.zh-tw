---
title: My.Response 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 2f72f493d99c1e0b0469150c041649486e5ed124
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818991"
---
# <a name="myresponse-object"></a>My.Response 物件
取得<xref:System.Web.HttpResponse>相關聯的物件<xref:System.Web.UI.Page>。 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。  
  
## <a name="remarks"></a>備註  
 `My.Response`物件包含目前<xref:System.Web.HttpResponse>與頁面關聯的物件。  
  
 `My.Response`僅適用於物件[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。  
  
## <a name="example"></a>範例  
 下列範例會取得從標頭集合`My.Request`物件，並使用`My.Response`物件寫入至 ASP.NET 網頁。  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Web.HttpResponse>
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
