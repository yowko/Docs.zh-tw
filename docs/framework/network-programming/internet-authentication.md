---
title: "網際網路驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fbf25ae866b338d2f1ac0ea11570e0d535e9137c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="internet-authentication"></a>網際網路驗證
<xref:System.Net> 類別支援各種不同的用戶端驗證機制，包括標準的網際網路驗證方法 (基本、摘要式、交涉式、NTLM 和 Kerberos 驗證) 以及您可以建立的自訂方法。  
  
 驗證認證儲存在 <xref:System.Net.NetworkCredential> 和 <xref:System.Net.CredentialCache> 類別中，能夠實作 <xref:System.Net.ICredentials> 介面。 當這些類別的其中之一經查詢認證後，它會傳回 **NetworkCredential** 類別的執行個體。 驗證程序是由 <xref:System.Net.AuthenticationManager> 類別管理，而實際的驗證程序是由實作 <xref:System.Net.IAuthenticationModule> 介面的驗證模組類別執行。 您必須先向 **AuthenticationManager** 註冊自訂的驗證模組才能使用它，預設會註冊基本、摘要式、交涉式、NTLM 和 Kerberos 驗證方法模組。  
  
 **NetworkCredential** 儲存了一組與 URI 所識別之單一網際網路資源建立關聯的認證，並傳回它們以回應 <xref:System.Net.NetworkCredential.GetCredential%2A> 方法的任何呼叫。 存取有限數量網際網路資源的應用程式，或在所有情況下使用同一組認證的應用程式，通常會使用 **NetworkCredential** 類別。  
  
 **CredentialCache** 類別儲存各種 Web 資源認證的集合。 呼叫 <xref:System.Net.CredentialCache.GetCredential%2A> 方法時，**CredentialCache** 會傳回適當的認證集，由 Web 資源 URI 和要求的驗證配置決定。 使用各種網際網路資源和不同驗證配置的應用程式，得益於使用 **CredentialCache** 類別，因為它會儲存所有認證並依要求提供認證。  
  
 當網際網路資源要求驗證時，<xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> 方法會將 <xref:System.Net.WebRequest> 以及認證要求傳送至 **AuthenticationManager**。 然後根據下列程序驗證要求：  
  
1.  **AuthenticationManager** 會在每個已註冊的驗證模組上，依其註冊順序呼叫 <xref:System.Net.IAuthenticationModule.Authenticate%2A> 方法。 **AuthenticationManager** 使用不會傳回 **null** 的第一個模組執行驗證程序。 程序的詳細資料隨所涉及的驗證模組類型而不同。  
  
2.  完成驗證程序後，驗證模組會將 <xref:System.Net.Authorization> 傳回至 **WebRequest**，後者包含存取網際網路資源所需的資訊。  
  
 某些驗證配置可以驗證使用者，不需要先要求資源。 應用程式可以預先驗證使用者和資源，至少消除一次伺服器往返，進而節省時間。 或者，它可以在程式啟動期間執行驗證，以便稍後更能回應使用者。 可以使用預先驗證的驗證配置，將 <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> 屬性設為 **true**。  
  
## <a name="see-also"></a>請參閱  
 [基本和摘要式驗證](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [NTLM 與 Kerberos 驗證](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [網路程式設計的安全性](../../../docs/framework/network-programming/security-in-network-programming.md)
