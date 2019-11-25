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
Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>. 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。  
  
## <a name="remarks"></a>備註  
 The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.  
  
 The `My.Response` object is only available for ASP.NET applications.  
  
## <a name="example"></a>範例  
 The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Web.HttpResponse>
- [My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)
