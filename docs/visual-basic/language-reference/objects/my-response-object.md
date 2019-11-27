---
title: My.Response 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 522814ad48fb7548032b8a37779bb3ff6ca62413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350650"
---
# <a name="myresponse-object"></a>My.Response 物件
取得與 <xref:System.Web.UI.Page>相關聯的 <xref:System.Web.HttpResponse> 物件。 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。  
  
## <a name="remarks"></a>備註  
 `My.Response` 物件包含與頁面相關聯的目前 <xref:System.Web.HttpResponse> 物件。  
  
 `My.Response` 物件僅適用于 ASP.NET 應用程式。  
  
## <a name="example"></a>範例  
 下列範例會從 `My.Request` 物件取得標頭集合，並使用 `My.Response` 物件將其寫入 ASP.NET 網頁。  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Web.HttpResponse>
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
