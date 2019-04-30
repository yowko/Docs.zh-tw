---
title: Unmanaged 程式碼的安全編碼指南
ms.date: 03/30/2017
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 138713c4a1397369ea18792a3b2742389b107a6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951706"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Unmanaged 程式碼的安全編碼指南
某些程式庫程式碼需要呼叫 Unmanaged 程式碼 (例如原生程式碼 API，像是 Win32)。 由於這表示要越過 Managed 程式碼的安全性範疇，所以充分的警告是必要的。 若您的程式碼是安全性中性的，則您的程式碼以及它所呼叫的任何程式碼，都必須具備 Unmanaged 程式碼權限 (指定了具有<xref:System.Security.Permissions.SecurityPermission> 旗標的 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> )。  
  
 不過對於您的呼叫端而言，擁有這類強大的權限並不合理。 在這種情況下，您信任的程式碼可做為中間人，類似 Managed 包裝函式或程式庫程式碼，如設定包裝函式程式碼的安全性 [Safe.GetTimeOfDay](../../../docs/framework/misc/securing-wrapper-code.md)所述。 如果基礎 Unmanaged 程式碼功能是完全安全的，則可以直接公開；否則，適當的權限檢查 (要求) 在第一次是必要的。  
  
 當您的程式碼呼叫 Unmanaged 程式碼，但您不想要求呼叫端擁有存取 Unmanaged 程式碼的權限時，則必須判斷提示該權限。 判斷提示會封鎖您框架上的堆疊查核行程。 您必須非常小心，不要在此處理序中建立安全性漏洞。 通常，這表示您必須要求呼叫端的適當權限，然後使用 Unmanaged 程式碼執行只有該權限所允許的動作。 在某些情況下 (例如取得一天中的時間之函式)，Unmanaged 程式碼可以直接公開給呼叫端，而不需任何安全性檢查。 在任何情況下，判斷提示的任何程式碼都必須確保安全。  
  
 由於提供進入原生程式碼的程式碼路徑之任何 Managed 程式碼都是惡意程式碼的潛在目標，所以必須特別小心地判斷哪些 Unmanaged 程式碼可以安全使用及如何使用。 一般而言，Unmanaged 程式碼應該永遠不會直接公開給部分信任呼叫端。 在可由部分信任程式碼呼叫的程式庫中，評估使用 Unmanaged 程式碼的安全性時，有兩個主要的考量：  
  
- 功能**Safe.GetTimeOfDay**。 Unmanaged 的 API 是否會提供功能，不允許呼叫端執行有潛在危險的作業？ 程式碼存取安全性會使用權限來強制執行資源的存取權，因此請考慮 API 是否使用檔案、使用者介面或執行緒處理，或是否會公開受保護的資訊。 若是如此，包裝它的 Managed 程式碼必須要求必要的權限，才能允許它進入。 此外，當不受權限保護時，記憶體存取必須限定為嚴格的類型安全。  
  
- 參數檢查**Safe.GetTimeOfDay**。 常見的攻擊會傳遞非預期的參數給公開的 Unmanaged 程式碼 API 方法，嘗試造成不合規格的運作。 使用超出範圍的索引或位移值的緩衝區滿溢是此類型攻擊的常見範例，就如可能會在基礎程式碼中惡意探索 Bug 的任何參數。 因此，即使 Unmanaged 程式碼 API 對於部分信任呼叫端在功能上是安全的 (在所需的要求之後)，Managed 程式碼仍必須徹底檢查參數有效性，以確保沒有可能來自使用 Managed 程式碼包裝函式層的惡意程式碼之非預期呼叫。  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>使用 SuppressUnmanagedCodeSecurityAttribute  
 有先判斷提示，然後再呼叫 Unmanaged 程式碼的效能層面。 對於每個這類呼叫，安全性系統會自動要求 Unmanaged 程式碼權限，每次都會導致堆疊查核行程。 如果您判斷提示，並立即呼叫 Unmanaged 程式碼，堆疊查核行程並無意義：它由您的判斷提示和 Unmanaged 程式碼呼叫所組成。  
  
 稱為 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 的自訂屬性可以套用至 Unmanaged 程式碼的進入點，以停用一般安全性檢查，該檢查會要求具有 <xref:System.Security.Permissions.SecurityPermission> 指定權限的 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 。 這樣做永遠都須特別小心，因為這個動作會為進入 Unmanaged 程式碼敞開大門，而不需執行階段安全性檢查。 請注意，即使套用 SuppressUnmanagedCodeSecurityAttribute **Safe.GetTimeOfDay** ，在 Just-In-Time (JIT) 編譯仍有單次安全性檢查，以確保立即呼叫者有權限呼叫 Unmanaged 程式碼。  
  
 如果您使用 SuppressUnmanagedCodeSecurityAttribute **Safe.GetTimeOfDay**，請檢查下列各點：  
  
- 讓 Unmanaged 程式碼進入點位於內部，否則在您的程式碼外部無法存取。  
  
- 對 Unmanaged 程式碼的任何呼叫都是潛在的安全性漏洞。 請確定您的程式碼並非惡意程式碼間接呼叫 Unmanaged 程式碼並躲避安全性檢查的入口。 請視情況要求權限。  
  
- 當您正在建立進入 Unmanaged 程式碼的危險路徑時，請使用命名慣例明確地識別，如下面小節所述。  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Unmanaged 程式碼方法的命名慣例  
 對於 Unmanaged 程式碼方法，已建立實用且強烈建議使用的命名慣例。 所有 Unmanaged 程式碼方法分為三個類別：安全 **Safe.GetTimeOfDay**、原生 **Native.Xyz**和不安全 **Unsafe.DangerousAPI**。 這些關鍵字可做為類別名稱，其中定義各種 Unmanaged 程式碼進入點的種類。 在原始程式碼中，這些關鍵字應該加入類別名稱，例如就像在 `Safe.GetTimeOfDay`、 `Native.Xyz`或 `Unsafe.DangerousAPI`中一樣。 這些關鍵字每個都會提供對於使用該類別的開發人員相當實用的安全性資訊，如下表所述。  
  
|關鍵字|安全性考量|  
|-------------|-----------------------------|  
|**Safe.GetTimeOfDay**|對於任何程式碼，即使是惡意程式碼，呼叫都完全無害。 就像其他 Managed 程式碼一樣可以使用。 例如，取得一天中的時間之函式通常都是安全的。|  
|**Native.Xyz**|安全性中性；也就是 Unmanaged 程式碼需要 Unmanaged 程式碼權限來呼叫。 會檢查安全性，這會停止未經授權的呼叫端。|  
|**Unsafe.DangerousAPI**|已隱藏安全性、有潛在危險的 Unmanaged 程式碼進入點。 當使用這類 Unmanaged 程式碼時，開發人員應高度警覺，確定其他保護已就位，以避免安全性弱點。 開發人員必須要負責，因為這個關鍵字會覆寫安全性系統。|  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
