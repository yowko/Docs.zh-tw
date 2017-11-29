---
title: "反映的安全性考量"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 756873e93d6e13cbb9077d10a52a718932afcedb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="security-considerations-for-reflection"></a>反映的安全性考量
反映可讓您取得類型和成員的相關資訊，以及存取成員 (也就是呼叫方法和建構函式、取得和設定屬性值、加入和移除事件處理常式等等)。 不限制使用反映來取得類型和成員的相關資訊。 所有程式碼都可以使用反映來執行下列工作：  
  
-   列舉類型和成員，並檢查其中繼資料。  
  
-   列舉及檢查組件和模組。  
  
 相對地，使用反映來存取成員有所限制。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，只有受信任的程式碼才能使用反映存取安全性關鍵成員。 此外，只有受信任的程式碼能夠使用反映來存取已編譯程式碼無法直接存取的非公用成員。 最後，使用反映存取安全性關鍵成員的程式碼必須擁有安全關鍵成員所要求的任何權限，就如同編譯的程式碼。  
  
 受限於所需的權限，程式碼可以使用反映來執行下列類型的存取：  
  
-   存取非安全性關鍵的公用成員。  
  
-   存取可供已編譯程式碼存取的非公用成員 (前提是這些成員不是安全性關鍵成員)。 這類非公用成員的範例包括：  
  
    -   呼叫程式碼基底類別的 Protected 成員。 (在反映中，這稱為系列層級的存取。)  
  
    -   呼叫程式碼組件中的 `internal` 成員 (在 Visual Basic 中為 `Friend` 成員)。 (在反映中，這稱為組件層級存取。)  
  
    -   包含呼叫程式碼之類別的其他執行個體的私用成員。  
  
 例如，在沙箱化應用程式定義域中執行的程式碼，僅限於此清單中所描述的存取權，除非應用程式定義域授與其他權限。  
  
 從 [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] 開始，嘗試存取通常無法存取的成員時，系統會要求目標物件的授權集，加上具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>。 以完全信任執行的程式碼 (例如從命令列啟動之應用程式中的程式碼)，一律可以滿足這些權限。 (這取決於存取安全性關鍵成員時的限制，本文稍後將會說明)。  
  
 (選擇性) 沙箱應用程式定義域可以授權有 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>，本文稍後的[存取通常無法存取的成員](#accessingNormallyInaccessible)一節將會說明。  
  
<a name="accessingSecurityCritical"></a>   
## <a name="accessing-security-critical-members"></a>存取安全性關鍵成員  
 如果成員有 <xref:System.Security.SecurityCriticalAttribute>、屬於具有 <xref:System.Security.SecurityCriticalAttribute> 的類型，或位於安全性關鍵組件中，就是安全性關鍵成員。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，存取安全性關鍵成員的規則如下：  
  
-   透明程式碼無法使用反映來存取安全性關鍵成員，即使是完全受信任的程式碼也一樣。 會擲回 <xref:System.MethodAccessException>、<xref:System.FieldAccessException> 或 <xref:System.TypeAccessException>。  
  
-   使用部分信任來執行的程式碼會視為透明。  
  
 無論是由已編譯程式碼直接存取安全性關鍵成員，或是使用反映來存取安全性關鍵成員，這些規則都一樣。  
  
 從命令列執行的應用程式程式碼會以完全信任來執行。 只要不是標示為透明，就可以使用反映來存取安全性關鍵成員。 以部分信任來執行相同的程式碼時 (例如，在沙箱化應用程式定義域中)，組件的信任層級可決定它是否能夠存取安全性關鍵程式碼：如果組件有強式名稱，並安裝在全域組件快取中，則其為受信任的組件，可以呼叫安全性關鍵成員。 如果不受信任，則會變成透明 (即使它不是標示為透明)，而且不能存取安全性關鍵成員。  
  
 如需 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 中安全性模型的詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。  
  
## <a name="reflection-and-transparency"></a>反映和透明度  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，Common Language Runtime 可以從數個因素來決定類型或成員的透明度，包括組件的信任層級和應用程式定義域的信任層級。 反映提供 <xref:System.Type.IsSecurityCritical%2A>、<xref:System.Type.IsSecuritySafeCritical%2A> 和 <xref:System.Type.IsSecurityTransparent%2A> 屬性，可讓您探索類型的透明度。 下表顯示這些屬性的有效組合。  
  
|安全性層級|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|  
|--------------------|------------------------|----------------------------|---------------------------|  
|Critical|`true`|`false`|`false`|  
|安全關鍵|`true`|`true`|`false`|  
|透明|`false`|`false`|`true`|  
  
 使用這些屬性會比檢查組件及其類型的安全性註釋、檢查目前的信任層級，以及嘗試複製執行階段規則更簡單。 例如，相同的類型從命令列執行時，就是安全性關鍵，在沙箱化應用程式定義域中執行時，就是安全性透明。  
  
 <xref:System.Reflection.MethodBase>、<xref:System.Reflection.FieldInfo>、<xref:System.Reflection.Emit.TypeBuilder>、<xref:System.Reflection.Emit.MethodBuilder> 和 <xref:System.Reflection.Emit.DynamicMethod> 類別上有類似的屬性。 (針對其他反映和反映發出抽象，安全性屬性 (security attribute) 會套用至相關聯的方法；例如，以屬性 (property) 來說，安全性屬性會套用至屬性存取子 (property accessor)。  
  
<a name="accessingNormallyInaccessible"></a>   
## <a name="accessing-members-that-are-normally-inaccessible"></a>存取通常無法存取的成員  
 若要使用反映來叫用無法存取的成員 (根據 Common Language Runtime 的存取範圍規則)，您的程式碼必須被授與下列兩個權限之一：  
  
-   若要允許程式碼叫用任何非公用成員：您的程式碼必須被授與具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>。  
  
    > [!NOTE]
    >  根據預設，安全性原則會拒絕將此權限授與源自網際網路的程式碼。 此權限絕不能授與源自網際網路的程式碼。  
  
-   若要允許程式碼叫用任何非公用成員，只要包含被叫用成員的組件授與集，與包含叫用程式碼的組件授與集相同，或是其授權集的子集：您的程式碼必須被授與具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標的  <xref:System.Security.Permissions.ReflectionPermission>。  
  
 例如，假設您將網際網路權限，以及具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>，授與應用程式定義域，然後執行網際網路應用程式來搭配兩個組件 A 和 B。  
  
-   組件 A 可以使用反映來存取組件 B 的私用成員，因為組件 B 的授權集不包含未授與 A 的任何權限。  
  
-   組件 A 無法使用反映來存取 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件的私用成員，例如 mscorlib.dll，因為 mscorlib.dll 是完全受信任，因此擁有尚未授與組件 A 的權限。當程式碼存取安全性查核執行階段的堆疊時，會擲回 <xref:System.MemberAccessException>。  
  
## <a name="serialization"></a>序列化  
 進行序列化時，不論存取範圍為何，具有 <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.SecurityPermission> 都可讓您取得或設定可序列化類型的成員。 此權限可讓程式碼探索及變更執行個體的私用狀態。 (除了授與適當的權限，也必須在中繼資料中將該類型[標示](../../../docs/standard/attributes/applying-attributes.md)為可序列化。)  
  
## <a name="parameters-of-type-methodinfo"></a>MethodInfo 類型的參數  
 避免撰寫採用 <xref:System.Reflection.MethodInfo> 參數的公用成員，特別是針對受信任的程式碼。 這類成員比較容易受到惡意程式碼攻擊。 例如，請考慮採用 <xref:System.Reflection.MethodInfo> 參數之高度信任程式碼中的公用成員。 假設公用成員在所提供的參數上間接呼叫 <xref:System.Reflection.MethodBase.Invoke%2A> 方法。 如果公用成員沒有執行必要的權限檢查，呼叫 <xref:System.Reflection.MethodBase.Invoke%2A> 方法一定會成功，因為安全性系統會判定呼叫者是受高度信任。 即使惡意程式碼沒有直接叫用方法的權限，它還是可以藉由呼叫公用成員來間接執行。  
  
## <a name="version-information"></a>版本資訊  
  
-   從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，透明程式碼無法使用反映來存取安全性關鍵的成員。  
  
-   [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] 中已開始使用 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標。 舊版 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 需要 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 旗標，使用反映的程式碼才能存取非公用成員。 絕不要將此權限授與部分受信任的程式碼。  
  
-   從 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 開始，使用反映來取得非公用類型和成員的相關資訊時，不需要任何權限。 在舊版中，會需要具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Security.Permissions.ReflectionPermissionFlag>  
 <xref:System.Security.Permissions.ReflectionPermission>  
 <xref:System.Security.Permissions.SecurityPermission>  
 [安全性變更](../../../docs/framework/security/security-changes.md)  
 [程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)  
 [反映發出中的安全性問題](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [套用屬性](../../../docs/standard/attributes/applying-attributes.md)  
 [存取自訂屬性](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)
