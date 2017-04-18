---
title: "Using Libraries from Partially Trusted Code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "security [.NET Framework], partially trusted code"
  - "partially trusted code"
  - "partial trust"
  - "AllowPartiallyTrustedCallersAttribute attribute"
  - "code access security, partially trusted code"
  - "APTCA"
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: 25
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 23
---
# Using Libraries from Partially Trusted Code
> [!NOTE]
>  本主題說明強式名稱組件的行為，並且只適用於[層級 1](../../../docs/framework/misc/security-transparent-code-level-1.md) 組件。[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 或更新版本中的組件 [Security\-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) 不會受到強式名稱影響。 如需安全性系統變更的相關資訊，請參閱 [安全性變更](../../../docs/framework/security/security-changes.md)。  
  
> [!CAUTION]
>  程式碼存取安全性和部分信任的程式碼  
>   
>  .NET Framework 提供一個稱為程式碼存取安全性 \(CAS\) 的機制，可對在同一個應用程式中執行的不同程式碼強制執行各種信任層級。  .NET Framework 中的程式碼存取安全性不應該做為部分信任的程式碼 \(特別是未知來源的程式碼\) 的安全性界限使用。 建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。  
>   
>  這項原則適用於所有 .NET Framework 版本，但不適用於 Silverlight 隨附的 .NET Framework。  
  
 從其主機或沙箱獲得低於完全信任的應用程式不允許呼叫共用 Managed 程式庫，除非程式庫撰寫者透過使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 來特別允許它們。 因此，應用程式撰寫者必須知道有些程式庫將無法從部分信任的內容使用它們。 根據預設，在部分信任的[沙箱](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)中執行並不在完全信任組件清單中的所有程式碼，會部分地受到信任。 如果您不希望從部分信任的內容中執行您的程式碼，或由部分信任程式碼呼叫您的程式碼，不必顧慮這一節中的資訊。 不過，如果您撰寫的程式碼必須與部分信任的程式碼互動，或從部分信任的內容操作，則應該考慮下列因素：  
  
-   程式庫必須使用強式名稱簽署，才能由多個應用程式共用。 強式名稱可讓您的程式碼放入全域組件快取，或加入沙箱環境 <xref:System.AppDomain> 的完全信任清單中，並允許取用者驗證行動程式碼的特定部分確實來自您。  
  
-   根據預設，使用強式名稱的[層級 1](../../../docs/framework/misc/security-transparent-code-level-1.md) 共用程式庫會自動執行完全信任的隱含 [LinkDemand](../../../docs/framework/misc/link-demands.md)，而不需要程式庫撰寫者執行任何動作。  
  
-   如果呼叫端沒有完全信任，但仍嘗試呼叫這類程式庫，執行階段會擲回 <xref:System.Security.SecurityException>，且不允許呼叫端連結程式庫。  
  
-   若要停用自動 **LinkDemand** 並避免擲回例外狀況，您可以使用共用程式庫的組件範圍上的 **AllowPartiallyTrustedCallersAttribute** 屬性。 此屬性允許從部分信任的 Managed 程式碼呼叫您的程式庫。  
  
-   以這個屬性被授權存取程式庫的部分信任程式碼，仍受限於 <xref:System.AppDomain> 定義的其他限制。  
  
-   部分信任程式碼沒有任何程式設計的方式可呼叫沒有 **AllowPartiallyTrustedCallersAttribute** 屬性的程式庫。  
  
 特定應用程式私用的程式庫不需要強式名稱或 **AllowPartiallyTrustedCallersAttribute** 屬性，且不能由應用程式外的可能惡意程式碼所參考。 這類程式碼受到保護可避免部分信任的行動程式碼有意或無意地誤用，而不需要開發人員執行任何額外的動作。  
  
 針對下列程式碼類型，您應該考慮明確地啟用部分信任程式碼的使用：  
  
-   程式碼已經過努力測試是否有安全性弱點，且符合[安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)中所述的方針。  
  
-   專為部分信任案例撰寫的強式名稱程式碼程式庫。  
  
-   使用強式名稱簽署，且將由從網際網路下載的程式碼呼叫的任何元件 \(不論部分或完全信任\)。  
  
> [!NOTE]
>  .NET Framework 類別庫中的某些類別沒有 **AllowPartiallyTrustedCallersAttribute** 屬性，而且無法由部分信任程式碼呼叫。  
  
## 請參閱  
 [Code Access Security](../../../docs/framework/misc/code-access-security.md)