---
title: 從部分受信任程式碼使用程式庫
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d32e5ed28153ae3ad54e1f75242a767d2e764a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585262"
---
# <a name="using-libraries-from-partially-trusted-code"></a>從部分受信任程式碼使用程式庫
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  本主題說明強式名稱組件的行為，並且只適用於[層級 1](../../../docs/framework/misc/security-transparent-code-level-1.md)組件。 [安全性透明程式碼，層級 2](../../../docs/framework/misc/security-transparent-code-level-2.md)中的組件[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]或更新版本不會受到強式名稱。 如需有關變更安全性系統的詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。  
  
 從其主機或沙箱獲得低於完全信任的應用程式不允許呼叫共用 Managed 程式庫，除非程式庫撰寫者透過使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 來特別允許它們。 因此，應用程式撰寫者必須知道有些程式庫將無法從部分信任的內容使用它們。 根據預設，所有的程式碼中執行部分信任[沙箱](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)並不是處於完全信任組件清單為部分信任。 如果您不希望從部分信任的內容中執行您的程式碼，或由部分信任程式碼呼叫您的程式碼，不必顧慮這一節中的資訊。 不過，如果您撰寫的程式碼必須與部分信任的程式碼互動，或從部分信任的內容操作，則應該考慮下列因素：  
  
-   程式庫必須使用強式名稱簽署，才能由多個應用程式共用。 強式名稱可讓您的程式碼放入全域組件快取，或加入沙箱環境 <xref:System.AppDomain> 的完全信任清單中，並允許取用者驗證行動程式碼的特定部分確實來自您。  
  
-   根據預設，強式名稱[層級 1](../../../docs/framework/misc/security-transparent-code-level-1.md)共用程式庫執行隱含[LinkDemand](../../../docs/framework/misc/link-demands.md)完全信任自動執行，而不需要執行任何動作的程式庫寫入器。  
  
-   如果呼叫端沒有完全信任，但仍嘗試呼叫這類程式庫，執行階段會擲回 <xref:System.Security.SecurityException>，且不允許呼叫端連結程式庫。  
  
-   若要停用自動**LinkDemand**並防止所擲回的例外狀況，您可以將放置**AllowPartiallyTrustedCallersAttribute**上共用的組件範圍的屬性程式庫。 此屬性允許從部分信任的 Managed 程式碼呼叫您的程式庫。  
  
-   以這個屬性被授權存取程式庫的部分信任程式碼，仍受限於 <xref:System.AppDomain> 定義的其他限制。  
  
-   沒有任何程式設計的方式，部分信任的程式碼呼叫的程式庫，並沒有**AllowPartiallyTrustedCallersAttribute**屬性。  
  
 私用特定的應用程式的程式庫不需要強式名稱或**AllowPartiallyTrustedCallersAttribute**屬性，而且無法由外部應用程式的潛在惡意程式碼參考。 這類程式碼受到保護可避免部分信任的行動程式碼有意或無意地誤用，而不需要開發人員執行任何額外的動作。  
  
 針對下列程式碼類型，您應該考慮明確地啟用部分信任程式碼的使用：  
  
-   程式碼已經過努力測試是否有安全性弱點，且符合所述的指導方針[安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)。  
  
-   專為部分信任案例撰寫的強式名稱程式碼程式庫。  
  
-   使用強式名稱簽署，且將由從網際網路下載的程式碼呼叫的任何元件 (不論部分或完全信任)。  
  
> [!NOTE]
>  .NET Framework 類別庫中的某些類別沒有**AllowPartiallyTrustedCallersAttribute**屬性，而且無法由部分信任程式碼呼叫。  
  
## <a name="see-also"></a>另請參閱
- [程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)
