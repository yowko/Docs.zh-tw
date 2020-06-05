---
title: My.Response 物件
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372452"
---
# <a name="myresponse-object"></a>My.Response 物件
取得 <xref:System.Web.HttpResponse> 與相關聯的物件 <xref:System.Web.UI.Page> 。 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。  
  
## <a name="remarks"></a>備註  
 `My.Response`物件包含 <xref:System.Web.HttpResponse> 與頁面相關聯的目前物件。  
  
 `My.Response`物件僅適用于 ASP.NET 應用程式。  
  
## <a name="example"></a>範例  
 下列範例會從物件取得標頭集合 `My.Request` ，並使用 `My.Response` 物件將其寫入至 ASP.NET 網頁。  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Web.HttpResponse>
- [My.Request 物件](my-request-object.md)
