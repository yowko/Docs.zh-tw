---
title: 設定包裝函式程式碼的安全性
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
ms.openlocfilehash: 3d38a4d4fd33798cf5987f5ce67305725ad9daec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399907"
---
# <a name="securing-wrapper-code"></a>設定包裝函式程式碼的安全性
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 包裝函式程式碼可能會導致出現一組獨特的安全性弱點，特別是當包裝函式的信任層級高於使用該包裝函式的程式碼時。 代表呼叫端執行任何作業時，由於適當的安全性檢查中不會包含呼叫端的限制權限，因此任何作業都有可能成為被惡意探索的弱點。  
  
 所以絕對不要透過包裝函式執行呼叫端本身無法執行的作業。 當執行的作業涉及有限制的安全性檢查時 (相對於完整堆疊查核行程要求)，這樣做會特別危險。 需要單一層級的檢查時，如果在真正的呼叫端和有問題的應用程式開發介面項目之間插入包裝函式程式碼，很容易造成安全性檢查在不該成功時卻成功完成，因而降低安全性。  
  
## <a name="delegates"></a>委派  
 不同的 .NET Framework 版本各有不同的委派安全性。  本節說明不同的委派行為及相關的安全性考量。  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>在 .NET Framework 1.0 和 1.1 版中  
 .NET Framework 1.0 和 1.1 版會對委派建立者和委派呼叫端執行下列安全性動作。  
  
- 建立委派時，會對委派建立者的授權集執行委派目標方法上的安全性連結要求。  無法滿足安全性動作會導致 <xref:System.Security.SecurityException>。  
  
- 叫用委派時，會執行委派呼叫端上任何現有的安全性要求。  
  
 當您的程式碼從可能呼叫它的較不受信任的程式碼接受 <xref:System.Delegate> 時，請務必不要讓較不受信任的程式碼提高它的權限。 如果您接受委派並在稍後使用它，建立該委派的程式碼就不會在呼叫堆疊上，而且如果委派中或之下的程式碼嘗試執行受保護的作業，也不會測試該程式碼的權限。 如果您的程式碼和呼叫端程式碼具有高於建立者的權限，則建立者不需要是呼叫堆疊的一部分，便可調整呼叫路徑。  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>在版本 2.0 和 .NET 框架的更高版本中  
 與以前的版本不同，創建和調用委託時，版本 2.0 和更高版本的 .NET Framework 對委託建立者執行安全操作。  
  
- 建立委派時，會對委派建立者的授權集執行委派目標方法上的安全性連結要求。  無法滿足安全性動作會導致 <xref:System.Security.SecurityException>。  
  
- 委派建立期間也會擷取委派建立者的授權集，並與委派一起儲存。  
  
- 叫用委派時，如果委派建立者和呼叫端各屬於不同的組件，就會先對目前內容中的任何要求評估委派建立者所擷取的授權集。  接著，便會執行委派呼叫端上任何現有的安全性要求。  
  
## <a name="link-demands-and-wrappers"></a>連結要求和包裝函式  
 我們已在安全性基礎結構中增強連結要求的特殊保護案例，但它仍然是您的程式碼中潛在弱點的來源。  
  
 如果完全受信任的代碼調用受[LinkDemand](link-demands.md)保護的屬性、事件或方法，則如果滿足調用方的**LinkDemand**許可權檢查，則調用將成功。 此外，如果完全受信任的代碼公開了獲取屬性名稱並使用反射調用其**get**訪問器的類，則對**get**訪問器的調用也會成功，即使使用者代碼無權訪問此屬性也是如此。 這是因為**LinkDemand**僅檢查直接調用方，即完全受信任的代碼。 本質上，完全受信任的程式碼是代表使用者程式碼進行有權限的呼叫，因此不需要確定使用者程式碼是否具有進行該呼叫的權限。  
  
 為了説明防止此類安全性漏洞，通用語言運行時將檢查擴展到對受**LinkDemand**保護的方法、建構函式、屬性或事件的任何間接調用上的完整堆疊遍線請求。 這項保護措施會稍微降低效能，也會變更安全性檢查的語意；較快的單一層級檢查可以通過的地方，完整堆疊查核行程要求卻有可能會失敗。  
  
## <a name="assembly-loading-wrappers"></a>組件載入包裝函式  
 有幾種用來載入 Managed 程式碼的方法 (包括 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>) 會使用呼叫端的辨識項載入組件。 如果您包裝任何方法，安全性系統就可以使用您的程式碼的權限授權 (而不是您包裝函式呼叫端的權限) 來載入組件。 您不應該允許較不受信任的程式碼載入權限高於您包裝函式呼叫端的程式碼。  
  
 擁有完全信任、或是比潛在呼叫端 (包括網際網路權限層級呼叫端) 更受信任的任何程式碼，都有可能因而降低安全性。 如果代碼具有一個公共方法，該方法採用位元組陣列並將其傳遞給**Assembly.Load，** 從而代表調用方創建程式集，則可能會破壞安全性。  
  
 這個問題會發生於下列應用程式開發介面項目：  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Demand 與LinkDemand 的比較  
 宣告式安全性提供兩種安全性檢查，這兩種安全性檢查雖然類似，但卻執行非常不同的檢查。 您應該了解這兩種形式，因為選擇錯誤可能導致安全性或效能低落。  
  
 宣告式安全性提供下列安全性檢查：  
  
- <xref:System.Security.Permissions.SecurityAction.Demand> 指定程式碼存取安全性堆疊查核行程。 堆疊上的所有呼叫端都必須具有指定的權限或識別，才能通過。 每個調用都會發生**請求**，因為堆疊可能包含不同的調用方。 如果您重複呼叫一個方法，則每呼叫一次就會執行這個安全性檢查一次。 **需求**是防止引誘攻擊的良好保護;未經授權的代碼試圖通過它將被檢測到。  
  
- [連結需求](link-demands.md)在即時 （JIT） 編譯時間發生，並且僅檢查直接調用方。 這項安全性檢查不會檢查呼叫端的呼叫端。 一旦通過這項檢查，不論呼叫端可能呼叫的次數為何，都不會再增加額外的安全性負荷。 不過，這也無法防止引誘攻擊。 使用**LinkDemand，** 任何通過測試並可以引用代碼的代碼都可能通過允許惡意程式碼使用授權代碼調用來破壞安全性。 因此，除非能夠徹底避免所有可能的弱點，否則不要使用**LinkDemand。**  
  
    > [!NOTE]
    > 在 .NET 框架 4 中，鏈路要求已被<xref:System.Security.SecurityCriticalAttribute>程式集中的<xref:System.Security.SecurityRuleSet.Level2>屬性替換。 <xref:System.Security.SecurityCriticalAttribute>相當於對完全信任的鏈路需求;但是，它也會影響繼承規則。 有關此更改的詳細資訊，請參閱[安全透明代碼，級別 2](security-transparent-code-level-2.md)。  
  
 使用**LinkDemand**時所需的額外預防措施必須單獨程式設計;安全系統可以説明執行。 任何錯誤都可能會導致出現安全性弱點。 使用您程式碼的所有授權程式碼都必須負責執行下列作業，以實作額外的安全性：  
  
- 限制呼叫的程式碼對類別或組件的存取。  
  
- 對呼叫的程式碼，套用出現在所呼叫之程式碼上的相同安全性檢查，並強制其呼叫端執行這項作業。 例如，如果編寫的代碼調用受指定<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>標誌的**LinkDemand**<xref:System.Security.Permissions.SecurityPermission>保護的方法，則方法還應為此許可權創建**LinkDemand（** 或 **"需求**"）。該許可權。 例外情況是，如果代碼使用**LinkDemand**保護方法的方式有限，您認為該方法是安全的，給定代碼中的其他安全保護機制（如需求）。 在這種例外狀況下，呼叫端會導致基礎程式碼的安全性保護變弱。  
  
- 確保您程式碼的呼叫端無法引誘您的程式碼代表呼叫端呼叫受保護的程式碼。 換句話說，呼叫端無法強制授權程式碼將特定參數傳遞給受保護的程式碼，或從中傳回結果。  
  
### <a name="interfaces-and-link-demands"></a>介面和連結要求  
 如果具有**LinkDemand**的虛擬方法、屬性或事件重寫基類方法，則基類方法還必須具有重寫方法的相同**LinkDemand，** 才能有效。 惡意程式碼可能會轉換回基底類型，並呼叫基底類別方法。 另請注意，連結要求可以隱含加入沒有 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 組件層級屬性的組件。  
  
 最佳做法是在介面方法也有連結要求時，使用連結要求來保護方法實作。 請注意下列有關搭配介面使用連結要求的資訊：  
  
- 如果將**LinkDemand**放置在實現介面方法的類的公共方法上，則如果隨後強制轉換為介面並調用該方法，則不會強制執行**LinkDemand。** 在這種情況下，由於您針對介面連結，因此僅尊重介面上的**LinkDemand。**  
  
 請檢閱下列安全性問題項目：  
  
- 介面方法上的明確連結要求。 確定這些連結要求提供預期的保護。 判斷惡意程式碼是否可以使用轉型來避開上述的連結要求。  
  
- 套用連結要求的虛擬方法。  
  
- 虛擬方法所實作的類型和介面。 這些類型和介面應該一致地使用連結要求。  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../standard/security/secure-coding-guidelines.md)
