---
title: "NTLM 與 Kerberos 驗證"
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c1662e5b0f8afd4ef92d2893a11c25457dbce024
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="045dd-102">NTLM 與 Kerberos 驗證</span><span class="sxs-lookup"><span data-stu-id="045dd-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="045dd-103">預設 NTLM 驗證和 Kerberos 驗證使用與呼叫端應用程式建立關聯的 Microsoft Windows NT 使用者認證，以嘗試向伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="045dd-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="045dd-104">使用非預設 NTLM 驗證時，應用程式會將驗證類型設為 NTLM，並使用 <xref:System.Net.NetworkCredential> 物件將使用者名稱、密碼和網域傳遞給主機，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="045dd-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="045dd-105">需要使用應用程式使用者認證來連線至網際網路服務的應用程式，可以利用使用者預設認證這麼做，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="045dd-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="045dd-106">交涉驗證模組可判斷遠端伺服器使用 NTLM 還是 Kerberos 驗證，並傳送適當的回應。</span><span class="sxs-lookup"><span data-stu-id="045dd-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="045dd-107">NTLM 驗證未透過 Proxy 伺服器進行運作。</span><span class="sxs-lookup"><span data-stu-id="045dd-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045dd-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="045dd-108">See Also</span></span>  
 [<span data-ttu-id="045dd-109">基本和摘要式驗證</span><span class="sxs-lookup"><span data-stu-id="045dd-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [<span data-ttu-id="045dd-110">網際網路驗證</span><span class="sxs-lookup"><span data-stu-id="045dd-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
