---
title: "網際網路驗證 | Microsoft Docs"
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
  - "IAuthenticationModule 介面"
  - "ICredentialLookup 介面"
  - "CredentialCache 類別，關於 CredentialCache 類別"
  - "接收資料，驗證"
  - "AuthenticationManager 類別，關於 AuthenticationManager 類別"
  - "網際網路，驗證"
  - "傳送資料，驗證"
  - "網路資源，驗證"
  - "使用者驗證，驗證的類別"
  - "NetworkCredential 類別，關於 NetworkCredential 類別"
  - "用戶端驗證，驗證的類別"
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 網際網路驗證
<xref:System.Net> 類別支援各種用戶端驗證機制，包括基本標準網際網路的驗證方法，摘要，交涉，、NTLM 和 Kerberos 驗證，以及您可以建立自訂的方法。  
  
 驗證認證。 <xref:System.Net.NetworkCredential> 和 <xref:System.Net.CredentialCache> 類別中，實作 <xref:System.Net.ICredentials> 介面。  當這些類別的其中一個用於驗證時進行查詢，則會傳回 **NetworkCredential** 類別的執行個體。  驗證處理序 <xref:System.Net.AuthenticationManager> 由類別處理，因此，實際驗證程序會實作介面的 <xref:System.Net.IAuthenticationModule> 驗證模組類別執行。  在使用之前，您必須向 **AuthenticationManager** 的自訂驗證模組它，基本的模組，摘要，交涉， NTLM，根據預設，和 Kerberos 驗證方法註冊。  
  
 **NetworkCredential** 儲存一組認證與 URI 所識別的單一網際網路資源並將它們以回應所有呼叫 <xref:System.Net.NetworkCredential.GetCredential%2A> 方法。  存取網際網路資源有限的或應用程式在所有的情況下使用同一組認證的應用程式通常會使用 **NetworkCredential** 類別。  
  
 **CredentialCache** 類別儲存認證的集合各種 Web 資源的。  當 <xref:System.Net.CredentialCache.GetCredential%2A> 呼叫方法時， **CredentialCache** 傳回適當認證組，由 Web 資源和要求的驗證配置的 URI。  使用不同的驗證配置的各種網際網路資源 **CredentialCache** 受益於使用類別的應用程式，，因為其中存放任何認證並提供它們要求。  
  
 在網際網路資源要求驗證時， <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=fullName> 方法傳送至 <xref:System.Net.WebRequest>**AuthenticationManager** 與要求一起認證。  需要根據下列處理序並驗證:  
  
1.  **AuthenticationManager** 會在每個上 <xref:System.Net.IAuthenticationModule.Authenticate%2A> 方法註冊的驗證模組可以根據其所註冊的順序。  **AuthenticationManager** 使用不傳回 **null** 執行驗證處理序的第一個模組。  處理序的細節會根據變更所涉及的驗證模組的型別。  
  
2.  當驗證程序已經完成時，會包含必要的資訊存取網際網路資源的驗證模組 <xref:System.Net.Authorization> 傳回至 **WebRequest** 。  
  
 某些驗證配置可以驗證使用者，而不需要先將資源的要求。  應用程式可以透過 preauthenticating 資源有使用者可以節省時間，以免至少一個來回存取伺服器。  或者，也可以稍後執行驗證在程式啟動期間為了可這麼做。  可使用預先驗證的驗證配置設定 [CanPreAuthenticate](frlrfsystemnetiauthenticationmoduleclasspreauthenticatetopic) 屬性設定為 **true**。  
  
## 請參閱  
 [基本和摘要式驗證](../../../docs/framework/network-programming/basic-and-digest-authentication.md)   
 [NTLM 與 Kerberos 驗證](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)   
 [網路程式設計的安全性](../../../docs/framework/network-programming/security-in-network-programming.md)