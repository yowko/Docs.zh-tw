---
title: "Security and Remoting Considerations | Microsoft Docs"
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
  - "code security, remoting"
  - "remoting, security"
  - "security [.NET Framework], remoting"
  - "secure coding, remoting"
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# Security and Remoting Considerations
遠端處理可讓您設定應用程式定義域、處理序或電腦之間的透明呼叫。  不過，程式碼存取安全性堆疊查核行程無法跨處理序或電腦界限 \(只會在同一個處理序的不同應用程式定義域之間套用\)。  
  
 所有可遠端處理的類別 \(衍生自 <xref:System.MarshalByRefObject> 類別\) 都必須確保安全。  程式碼應該只在可隱含信任呼叫端程式碼的封閉式環境中使用，或者遠端處理呼叫的設計方式，應該使受保護的程式碼不容易遭到惡意使用之外部項目的攻擊。  
  
 一般而言，您絕不能公開受宣告式 [LinkDemand](../../../docs/framework/misc/link-demands.md) 和 <xref:System.Security.Permissions.SecurityAction> 安全性檢查保護的方法、屬性或事件。  進行遠端處理時，系統不會強制執行這些檢查。  其他安全性檢查 \(例如 <xref:System.Security.Permissions.SecurityAction>、[Assert](../../../docs/framework/misc/using-the-assert-method.md) 等\) 可在同一個處理序的不同應用程式定義域之間執行，但不能在跨處理序或跨電腦的情況下執行。  
  
## 受保護的物件  
 某些物件本身有安全性狀態。  這些物件不應該傳遞至不受信任的程式碼，這類程式碼可能會接著取得超出其所有權限的安全性授權。  
  
 建立 <xref:System.IO.FileStream> 物件即為一例。  建立該物件時需要 <xref:System.Security.Permissions.FileIOPermission>；如果成功，則會傳回檔案物件。  不過，如果在未提供檔案權限的情況下，將這個物件參考傳遞至程式碼，則能夠從這個特定檔案讀取物件並將物件寫入檔案。  
  
 保護這類物件的最簡單做法，是針對試圖透過公用應用程式開發介面項目取得物件參考的所有程式碼，要求相同的 **FileIOPermission**。  
  
## 跨應用程式定義域的問題  
 若要將程式碼隔離到 Managed 裝載環境中，通常會產生多個子應用程式定義域，這些應用程式定義域具有降低各種組件之權限層級的明確原則。  不過，這些組件的原則在預設應用程式定義域中會保持不變。  如果其中一個子應用程式定義域可強制預設應用程式定義域載入組件，則會失去程式碼隔離的效果，而且強制載入之組件中的類型將能夠在較高的信任層級執行程式碼。  
  
 應用程式定義域可強制另一個應用程式定義域載入組件，並透過呼叫另一個應用程式定義域所裝載的物件 Proxy，來執行包含在組件中的程式碼。  若要取得跨應用程式定義域的 Proxy，裝載該物件的應用程式定義域必須透過方法呼叫參數或傳回值來發佈一個 Proxy。  或者，如果剛建立應用程式定義域，則建立者預設會有 <xref:System.AppDomain> 物件的 Proxy。  因此，為了避免破壞程式碼隔離，信任層級較高的應用程式定義域不應該將以傳址方式封送處理的物件參考 \(衍生自 <xref:System.MarshalByRefObject> 的類別執行個體\)，從其定義域散發到信任層級較低的應用程式定義域。  
  
 預設應用程式定義域在建立子應用程式定義域時，通常會在每個子應用程式定義域中包含一個控制項物件。  這個控制項物件會管理新的應用程式定義域，有時會接受來自預設應用程式定義域的命令，但實際上不會直接連絡定義域。  預設應用程式定義域有時會對控制項物件呼叫其 Proxy。  不過也有些情況，必須對預設應用程式定義域回呼控制項物件。  在這些情況下，預設應用程式定義域會將以傳址方式封送處理的回呼物件，傳遞給控制項物件的建構函式。  再由控制項物件負責保護這個 Proxy。  如果控制項物件將 Proxy 放在公用類別的公用靜態欄位上，或公開 Proxy，可能會危害機制，導致對預設應用程式定義域回呼其他程式碼。  因此，控制項物件一律會受到隱含信任，以保密 Proxy。  
  
## 請參閱  
 [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md)