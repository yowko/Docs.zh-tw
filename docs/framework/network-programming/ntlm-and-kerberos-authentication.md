---
title: NTLM 與 Kerberos 驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: ca9e1b9bf6235fdaeea25b8975155af429848ae3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047532"
---
# <a name="ntlm-and-kerberos-authentication"></a>NTLM 與 Kerberos 驗證
預設 NTLM 驗證和 Kerberos 驗證使用與呼叫端應用程式建立關聯的 Microsoft Windows NT 使用者認證，以嘗試向伺服器進行驗證。 使用非預設 NTLM 驗證時，應用程式會將驗證類型設為 NTLM，並使用 <xref:System.Net.NetworkCredential> 物件將使用者名稱、密碼和網域傳遞給主機，如下列範例所示。  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 需要使用應用程式使用者認證來連線至網際網路服務的應用程式，可以利用使用者預設認證這麼做，如下列範例所示。  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 交涉驗證模組可判斷遠端伺服器使用 NTLM 還是 Kerberos 驗證，並傳送適當的回應。  
  
> [!NOTE]
> NTLM 驗證未透過 Proxy 伺服器進行運作。  
  
## <a name="see-also"></a>另請參閱

- [基本和摘要式驗證](basic-and-digest-authentication.md)
- [網際網路驗證](internet-authentication.md)
