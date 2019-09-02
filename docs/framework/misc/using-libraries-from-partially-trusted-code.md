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
ms.openlocfilehash: 50428e4e28df812a3a0c985d0d1876dab7b5279c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206024"
---
# <a name="using-libraries-from-partially-trusted-code"></a>從部分受信任程式碼使用程式庫
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> 本主題說明強式名稱元件的行為, 並且只適用于[層級 1](security-transparent-code-level-1.md)元件。 [安全性透明的程式碼、](security-transparent-code-level-2.md) .NET Framework 4 或更新版本中的層級2元件不會受到強式名稱的影響。 如需安全性系統變更的詳細資訊, 請參閱[安全性變更](../security/security-changes.md)。  
  
 從其主機或沙箱獲得低於完全信任的應用程式不允許呼叫共用 Managed 程式庫，除非程式庫撰寫者透過使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 來特別允許它們。 因此，應用程式撰寫者必須知道有些程式庫將無法從部分信任的內容使用它們。 根據預設, 在部分信任的[沙箱](how-to-run-partially-trusted-code-in-a-sandbox.md)中執行且不在完全信任元件清單中的所有程式碼, 都是部分信任的。 如果您不希望從部分信任的內容中執行您的程式碼，或由部分信任程式碼呼叫您的程式碼，不必顧慮這一節中的資訊。 不過，如果您撰寫的程式碼必須與部分信任的程式碼互動，或從部分信任的內容操作，則應該考慮下列因素：  
  
- 程式庫必須使用強式名稱簽署，才能由多個應用程式共用。 強式名稱可讓您的程式碼放入全域組件快取，或加入沙箱環境 <xref:System.AppDomain> 的完全信任清單中，並允許取用者驗證行動程式碼的特定部分確實來自您。  
  
- 根據預設, 強式名稱[層級 1](security-transparent-code-level-1.md)共用程式庫會自動執行完全信任的隱含[LinkDemand](link-demands.md) , 而不需要程式庫撰寫者執行任何動作。  
  
- 如果呼叫端沒有完全信任，但仍嘗試呼叫這類程式庫，執行階段會擲回 <xref:System.Security.SecurityException>，且不允許呼叫端連結程式庫。  
  
- 若要停用自動**LinkDemand**並防止擲回例外狀況, 您可以將**AllowPartiallyTrustedCallersAttribute**屬性放在共用程式庫的元件範圍上。 此屬性允許從部分信任的 Managed 程式碼呼叫您的程式庫。  
  
- 以這個屬性被授權存取程式庫的部分信任程式碼，仍受限於 <xref:System.AppDomain> 定義的其他限制。  
  
- 部分信任的程式碼沒有任何程式設計的方式可呼叫沒有**AllowPartiallyTrustedCallersAttribute**屬性的程式庫。  
  
 特定應用程式私用的程式庫不需要強名稱或**AllowPartiallyTrustedCallersAttribute**屬性, 而且不能由應用程式外部的潛在惡意程式碼參考。 這類程式碼受到保護可避免部分信任的行動程式碼有意或無意地誤用，而不需要開發人員執行任何額外的動作。  
  
 針對下列程式碼類型，您應該考慮明確地啟用部分信任程式碼的使用：  
  
- 已針對安全性弱點進行過仔細測試的程式碼, 並遵循安全程式碼撰寫[方針](../../standard/security/secure-coding-guidelines.md)中所述的指導方針。  
  
- 專為部分信任案例撰寫的強式名稱程式碼程式庫。  
  
- 使用強式名稱簽署，且將由從網際網路下載的程式碼呼叫的任何元件 (不論部分或完全信任)。  
  
> [!NOTE]
> .NET Framework Class Library 中的某些類別沒有**AllowPartiallyTrustedCallersAttribute**屬性, 而且無法由部分信任的程式碼呼叫。  
  
## <a name="see-also"></a>另請參閱

- [程式碼存取安全性](code-access-security.md)
