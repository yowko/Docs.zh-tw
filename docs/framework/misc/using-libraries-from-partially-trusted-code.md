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
ms.openlocfilehash: 61291a07639c3f92a05f78dff49f6b20f1aee77e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645724"
---
# <a name="using-libraries-from-partially-trusted-code"></a>從部分受信任程式碼使用程式庫
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> 本主題討論強命名程式集的行為,並且僅適用於[級別 1](security-transparent-code-level-1.md)程式集。 [安全透明代碼、.NET](security-transparent-code-level-2.md)框架 4 或更高版本中的 2 級程式集不受強名稱的影響。 有關安全系統更改的詳細資訊,請參閱[安全變更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)。  
  
 從其主機或沙箱獲得低於完全信任的應用程式不允許呼叫共用 Managed 程式庫，除非程式庫撰寫者透過使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 來特別允許它們。 因此，應用程式撰寫者必須知道有些程式庫將無法從部分信任的內容使用它們。 預設情況下,在部分信任[沙箱](how-to-run-partially-trusted-code-in-a-sandbox.md)中執行且不在完全信任程式集清單中的所有代碼都是部分受信任的。 如果您不希望從部分信任的內容中執行您的程式碼，或由部分信任程式碼呼叫您的程式碼，不必顧慮這一節中的資訊。 不過，如果您撰寫的程式碼必須與部分信任的程式碼互動，或從部分信任的內容操作，則應該考慮下列因素：  
  
- 程式庫必須使用強式名稱簽署，才能由多個應用程式共用。 強式名稱可讓您的程式碼放入全域組件快取，或加入沙箱環境 <xref:System.AppDomain> 的完全信任清單中，並允許取用者驗證行動程式碼的特定部分確實來自您。  
  
- 默認情況下,強名稱的[1 級](security-transparent-code-level-1.md)共用庫自動執行隱式[LinkDemand](link-demands.md)以完全信任,而庫編寫器無需執行任何操作。  
  
- 如果呼叫端沒有完全信任，但仍嘗試呼叫這類程式庫，執行階段會擲回 <xref:System.Security.SecurityException>，且不允許呼叫端連結程式庫。  
  
- 為了禁用自動**LinkDemand**並防止引發異常,可以將**Allow 部分受信任的調用方屬性**放在共用庫的程式集作用域上。 此屬性允許從部分信任的 Managed 程式碼呼叫您的程式庫。  
  
- 以這個屬性被授權存取程式庫的部分信任程式碼，仍受限於 <xref:System.AppDomain> 定義的其他限制。  
  
- 沒有程式設計方式讓部分受信任的代碼呼叫沒有 **「允許部分受信任的呼叫方屬性」屬性**的庫。  
  
 專用到特定應用程式的庫不需要強名稱或**AllowPartiallyTrustedCallers 屬性**,並且應用程式外部的潛在惡意代碼無法引用。 這類程式碼受到保護可避免部分信任的行動程式碼有意或無意地誤用，而不需要開發人員執行任何額外的動作。  
  
 針對下列程式碼類型，您應該考慮明確地啟用部分信任程式碼的使用：  
  
- 已對安全漏洞進行認真測試並符合[安全編碼指南中描述的準則](../../standard/security/secure-coding-guidelines.md)的代碼。  
  
- 專為部分信任案例撰寫的強式名稱程式碼程式庫。  
  
- 使用強式名稱簽署，且將由從網際網路下載的程式碼呼叫的任何元件 (不論部分或完全信任)。  
  
> [!NOTE]
> .NET Framework 類庫中的某些類沒有 **"允許部分受信任的調用方屬性"屬性**,並且無法由部分受信任的代碼調用。  
  
## <a name="see-also"></a>另請參閱

- [代碼存取安全性](code-access-security.md)
