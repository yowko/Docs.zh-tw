---
title: "NTLM 與 Kerberos 驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "驗證 [.NET Framework]，NTLM"
  - "驗證 [.NET Framework]，Kerberos"
  - "使用者驗證，Kerberos"
  - "使用者驗證，NTLM"
  - "Kerberos 驗證"
  - "接收資料，驗證"
  - "NTLM 驗證"
  - "網際網路，驗證"
  - "用戶端驗證，Kerberos"
  - "傳送資料，驗證"
  - "網路資源，驗證"
  - "類別 [.NET Framework]，驗證"
  - "用戶端驗證，NTLM"
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# NTLM 與 Kerberos 驗證
預設 NTLM 驗證，並且 Kerberos Microsoft Windows NT 使用者認證與呼叫的應用程式嘗試與伺服器上執行驗證的驗證使用。  如下列範例所示，當使用非預設的 NTLM 驗證時，應用程式設定驗證類型為 NTLM 並使用 <xref:System.Net.NetworkCredential> 物件傳遞使用者名稱、密碼和網域加入至主應用程式。  
  
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
  
 需要連接至網際網路服務使用應用程式使用者的認證，如下列範例所示的應用程式就可以與使用者的預設認證，。  
  
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
  
 交涉驗證模組判斷遠端伺服器是否使用 NTLM 或 Kerberos 驗證，並傳送適當的回應。  
  
> [!NOTE]
>  NTLM 驗證不會透過 Proxy 伺服器運作。  
  
## 請參閱  
 [基本和摘要式驗證](../../../docs/framework/network-programming/basic-and-digest-authentication.md)   
 [網際網路驗證](../../../docs/framework/network-programming/internet-authentication.md)