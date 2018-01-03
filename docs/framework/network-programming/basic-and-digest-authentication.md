---
title: "基本和摘要式驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7ca66a65c05da3d515358c0fdb26682fa4ec1438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="basic-and-digest-authentication"></a>基本和摘要式驗證
基本和摘要式驗證的 <xref:System.Net> 實作符合 RFC2617 - HTTP 驗證：基本和摘要式驗證 (可在全球資訊網協會的網站 www.w3.org 上取得)。  
  
 若要使用基本和摘要式驗證，應用程式必須在 <xref:System.Net.WebRequest> 物件的 <xref:System.Net.WebRequest.Credentials%2A> 屬性中提供使用者名稱和密碼，以用來從網際網路要求資料，如下列範例所示。  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
>  使用基本與摘要式驗證傳送的資料不會經過加密，因此敵人可以看到資料。 此外，基本驗證認證 (使用者名稱和密碼) 會以純文字傳送，而且可以被攔截。  
  
## <a name="see-also"></a>請參閱  
 [NTLM 與 Kerberos 驗證](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [網際網路驗證](../../../docs/framework/network-programming/internet-authentication.md)
