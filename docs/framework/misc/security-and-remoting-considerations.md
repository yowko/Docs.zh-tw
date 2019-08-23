---
title: 安全性和遠端處理考量
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb5727bab8e06decde6ccff8b84515f82c3d491a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910697"
---
# <a name="security-and-remoting-considerations"></a>安全性和遠端處理考量
遠端處理可讓您設定應用程式定義域、處理序或電腦之間的透明呼叫。 不過，程式碼存取安全性堆疊查核行程無法跨處理序或電腦界限 (只會在同一個處理序的不同應用程式定義域之間套用)。  
  
 所有可遠端處理的類別 (衍生自 <xref:System.MarshalByRefObject> 類別) 都必須確保安全。 程式碼應該只在可隱含信任呼叫端程式碼的封閉式環境中使用，或者遠端處理呼叫的設計方式，應該使受保護的程式碼不容易遭到惡意使用之外部項目的攻擊。  
  
 一般來說, 您絕對不應該公開受宣告式[LinkDemand](../../../docs/framework/misc/link-demands.md)和<xref:System.Security.Permissions.SecurityAction.InheritanceDemand>安全性檢查保護的方法、屬性或事件。 進行遠端處理時，系統不會強制執行這些檢查。 其他安全性檢查 (例如<xref:System.Security.Permissions.SecurityAction.Demand>、 [Assert](../../../docs/framework/misc/using-the-assert-method.md)等) 可在進程內的應用程式域之間執行, 但不能在跨進程或跨電腦的情況下使用。  
  
## <a name="protected-objects"></a>受保護的物件  
 某些物件本身有安全性狀態。 這些物件不應該傳遞至不受信任的程式碼，這類程式碼可能會接著取得超出其所有權限的安全性授權。  
  
 建立 <xref:System.IO.FileStream> 物件即為一例。 建立該物件時需要 <xref:System.Security.Permissions.FileIOPermission>；如果成功，則會傳回檔案物件。 不過，如果在未提供檔案權限的情況下，將這個物件參考傳遞至程式碼，則能夠從這個特定檔案讀取物件並將物件寫入檔案。  
  
 這類物件最簡單的防禦, 就是要求任何程式碼的相同**FileIOPermission** , 以透過公用 API 元素取得物件參考。  
  
## <a name="application-domain-crossing-issues"></a>跨應用程式定義域的問題  
 若要將程式碼隔離到 Managed 裝載環境中，通常會產生多個子應用程式定義域，這些應用程式定義域具有降低各種組件之權限層級的明確原則。 不過，這些組件的原則在預設應用程式定義域中會保持不變。 如果其中一個子應用程式定義域可強制預設應用程式定義域載入組件，則會失去程式碼隔離的效果，而且強制載入之組件中的類型將能夠在較高的信任層級執行程式碼。  
  
 應用程式定義域可強制另一個應用程式定義域載入組件，並透過呼叫另一個應用程式定義域所裝載的物件 Proxy，來執行包含在組件中的程式碼。 若要取得跨應用程式定義域的 Proxy，裝載該物件的應用程式定義域必須透過方法呼叫參數或傳回值來發佈一個 Proxy。 或者，如果剛建立應用程式定義域，則建立者預設會有 <xref:System.AppDomain> 物件的 Proxy。 因此，為了避免破壞程式碼隔離，信任層級較高的應用程式定義域不應該將以傳址方式封送處理的物件參考 (衍生自 <xref:System.MarshalByRefObject> 的類別執行個體)，從其定義域散發到信任層級較低的應用程式定義域。  
  
 預設應用程式定義域在建立子應用程式定義域時，通常會在每個子應用程式定義域中包含一個控制項物件。 這個控制項物件會管理新的應用程式定義域，有時會接受來自預設應用程式定義域的命令，但實際上不會直接連絡定義域。 預設應用程式定義域有時會對控制項物件呼叫其 Proxy。 不過也有些情況，必須對預設應用程式定義域回呼控制項物件。 在這些情況下，預設應用程式定義域會將以傳址方式封送處理的回呼物件，傳遞給控制項物件的建構函式。 再由控制項物件負責保護這個 Proxy。 如果控制項物件將 Proxy 放在公用類別的公用靜態欄位上，或公開 Proxy，可能會危害機制，導致對預設應用程式定義域回呼其他程式碼。 因此，控制項物件一律會受到隱含信任，以保密 Proxy。  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../standard/security/secure-coding-guidelines.md)
