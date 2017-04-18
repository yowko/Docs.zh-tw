---
title: "基本和摘要式驗證 | Microsoft Docs"
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
  - "驗證 [.NET Framework]，類別"
  - "基本驗證"
  - "驗證 [.NET Framework]，基本"
  - "用戶端驗證，基本"
  - "使用者驗證，基本"
  - "驗證 [.NET Framework]，摘要式"
  - "接收資料，驗證"
  - "用戶端驗證，摘要式"
  - "網際網路，驗證"
  - "摘要式驗證"
  - "傳送資料，驗證"
  - "網路資源，驗證"
  - "使用者驗證，摘要式"
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 基本和摘要式驗證
基本和摘要式驗證的 <xref:System.Net> 實作符合 RFC2617 – HTTP Authentication:基本和摘要式驗證 \(可以在全球資訊網協會 \(W3C\) 網站上 www.w3.org \(英文\)。  
  
 如下列範例所示，若要使用基本和摘要式驗證，應用程式必須提供使用者名稱和密碼會使用要求資料從網際網路 <xref:System.Net.WebRequest> 物件的 <xref:System.Net.WebRequest.Credentials%2A> 屬性。  
  
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
>  所傳送之資料的基本和摘要式驗證不會加密，因此，資料可以被敵人參閱。  此外，基本驗證認證 \(使用者名稱和密碼\) 的危險傳送並可以攔截。  
  
## 請參閱  
 [NTLM 與 Kerberos 驗證](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)   
 [網際網路驗證](../../../docs/framework/network-programming/internet-authentication.md)