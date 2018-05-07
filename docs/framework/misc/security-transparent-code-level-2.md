---
title: 安全性透明的程式碼，層級 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f15c3bc097bc034db41c95cd168104b8435aaf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="security-transparent-code-level-2"></a>安全性透明的程式碼，層級 2
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 層級 2 透明度是 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 引入的。 此模型的三個原則是透明程式碼、安全性安全關鍵程式碼和安全性關鍵程式碼。  
  
-   透明程式碼，包括以完全信任執行的程式碼，只可以呼叫其他透明程式碼或安全性安全關鍵程式碼。 它只能執行定義域之部分信任權限集合 (如果存在的話) 所允許的動作。 透明程式碼無法進行下列作業：  
  
    -   執行 <xref:System.Security.CodeAccessPermission.Assert%2A> 或提高權限。  
  
    -   包含不安全或無法驗證的程式碼。  
  
    -   直接呼叫關鍵程式碼。  
  
    -   呼叫機器碼或含有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性的程式碼。  
  
    -   呼叫 <xref:System.Security.Permissions.SecurityAction.LinkDemand> 所保護的成員。  
  
    -   繼承自關鍵類型。  
  
     此外，透明方法無法覆寫關鍵虛擬方法或實作關鍵介面方法。  
  
-   安全關鍵程式碼受到完全信任，但是可由透明程式碼呼叫。 它會公開完全信任程式碼的有限介面區；正確性和安全性驗證會在安全關鍵程式碼中進行。  
  
-   雖然安全性關鍵程式碼可以呼叫任何程式碼，而且受到完全信任，但是無法由透明程式碼呼叫。  
  
 此主題包括下列章節：  
  
-   [使用範例和行為](#examples)  
  
-   [覆寫模式](#override)  
  
-   [繼承規則](#inheritance)  
  
-   [其他資訊和規則](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a>使用範例和行為  
 若要指定 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 規則 (層級 2 透明度)，請針對組件使用下列註釋：  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 若要鎖定 .NET Framework 2.0 規則 (層級 1 透明度)，請使用下列註釋：  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 如果您沒有為組件加上附註，預設將使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 規則。 不過，建議的最佳作法是使用<xref:System.Security.SecurityRulesAttribute>屬性，而非仰賴預設值。  
  
### <a name="assembly-wide-annotation"></a>組件範圍的註釋  
 下列規則適用於在組件層級使用屬性：  
  
-   無屬性：如果您沒有指定任何屬性，執行階段就會將所有程式碼解譯為安全性關鍵的，但是安全性關鍵違反繼承規則的程式碼除外 (例如，在覆寫或實作透明虛擬或介面方法時)。 在這些情況下，這些方法都是安全關鍵方法。 不指定屬性會導致 Common Language Runtime 為您決定透明度規則。  
  
-   `SecurityTransparent`：所有程式碼都是透明的；整個組件將不會進行任何需要權限或不安全的作業。  
  
-   `SecurityCritical`：這個組件中類型所引入的所有程式碼都是關鍵的；所有其他程式碼則為透明的。 這個案例與不指定任何屬性很相似；不過，Common Language Runtime 不會自動決定透明度規則。 例如，如果您覆寫虛擬或抽象方法，或是實作介面方法，則根據預設，該方法為透明的。 您必須明確將此方法加註為 `SecurityCritical` 或 `SecuritySafeCritical`；否則，系統將在載入時擲回 <xref:System.TypeLoadException>。 當基底類別和衍生類別都位於相同的組件時，這項規則也適用。  
  
-   `AllowPartiallyTrustedCallers` (僅限層級 2)：所有程式碼都預設為透明的。 不過，個別的類型和成員可以有其他屬性。  
  
 下表會比較層級 2 與層級 1 組件層級行為。  
  
|Assembly 屬性|階層 2|階層 1|  
|------------------------|-------------|-------------|  
|部分信任組件無屬性|根據預設，類型和成員為透明的，但是可能為安全性關鍵或安全性安全關鍵的。|所有類型和成員皆為透明的。|  
|無屬性|不指定屬性會導致 Common Language Runtime 為您決定透明度規則。 所有類型和成員都是安全性關鍵的，但是安全性關鍵違反繼承規則的程式碼除外。|在完全信任的組件上 (位於全域組件快取中或在 `AppDomain` 中識別為完全信任)，所有類型都是透明的，而且所有成員都是安全性安全關鍵的。|  
|`SecurityTransparent`|所有類型和成員皆為透明的。|所有類型和成員皆為透明的。|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|不適用。|所有類型和成員皆為安全性關鍵的。|  
|`SecurityCritical`|這個組件中之類型所引入的所有程式碼都是關鍵的；所有其他程式碼則為透明的。 如果您覆寫虛擬或抽象方法，或是實作介面方法，就必須明確將此方法加註為 `SecurityCritical` 或 `SecuritySafeCritical`。|所有程式碼都預設為透明的。 不過，個別的類型和成員可以有其他屬性。|  
  
### <a name="type-and-member-annotation"></a>類型和成員註釋  
 套用至某個類型的安全性屬性也會套用至該類型所引入的成員。 不過，這些屬性不會套用至基底類別或介面實作的虛擬或抽象覆寫。 下列規則適用於在類型和成員層級使用屬性：  
  
-   `SecurityCritical`：類型或成員是關鍵的，而且只能由完全信任程式碼呼叫。 在安全性關鍵類型中引入的方法是關鍵的。  
  
    > [!IMPORTANT]
    >  根據預設，在基底類別或介面中引入，並且在安全性關鍵類別中覆寫或實作的虛擬和抽象方法為透明的。 它們必須識別為 `SecuritySafeCritical` 或 `SecurityCritical`。  
  
-   `SecuritySafeCritical`：類型或成員是安全關鍵的。 不過，此類型或成員可以從透明 (部分信任) 程式碼呼叫，而且其功能與任何其他關鍵程式碼一樣。 基於安全性，您必須稽核此程式碼。  
  
 [回到頁首](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a>覆寫模式  
 下表顯示層級 2 透明度所允許的方法覆寫。  
  
|基底虛擬/介面成員|覆寫/介面|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [回到頁首](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a>繼承規則  
 在本節中，下列順序是根據存取和功能指派給 `Transparent`、`Critical` 和 `SafeCritical` 程式碼：  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   類型的規則：由左至右執行，存取限制變得更嚴格。 衍生類型的限制至少必須與基底類型一樣嚴格。  
  
-   方法的規則：衍生方法無法變更基底方法的存取範圍。 就預設行為而言，沒有加上附註的所有衍生方法都是 `Transparent`。 如果覆寫方法沒有明確加註為 `SecurityCritical`，關鍵類型的衍生物會導致系統擲回例外狀況。  
  
 下表顯示允許的類型繼承模式。  
  
|基底類別|衍生類別可為|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 下表顯示不允許的類型繼承模式。  
  
|基底類別|衍生類別不可為|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 下表顯示允許的方法繼承模式。  
  
|基底方法|衍生方法可為|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 下表顯示不允許的方法繼承模式。  
  
|基底方法|衍生方法不可為|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  這些繼承規則適用於層級 2 類型和成員。 層級 1 組件中的類型可以繼承自層級 2 安全性關鍵類型和成員。 因此，層級 2 類型和成員必須針對層級 1 繼承者具有不同的繼承要求。  
  
 [回到頁首](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a>其他資訊和規則  
  
### <a name="linkdemand-support"></a>LinkDemand 支援  
 層級 2 透明度模型會將 <xref:System.Security.Permissions.SecurityAction.LinkDemand> 取代成 <xref:System.Security.SecurityCriticalAttribute> 屬性。 在舊版 (層級 1) 程式碼中，<xref:System.Security.Permissions.SecurityAction.LinkDemand> 可自動視為 <xref:System.Security.Permissions.SecurityAction.Demand>。  
  
### <a name="reflection"></a>反射  
 叫用關鍵方法或讀取關鍵欄位就會觸發完全信任的要求 (就如同您叫用私用方法或欄位一樣)。 因此，完全信任程式碼可以叫用關鍵方法，而部分信任程式碼則無法叫用。  
  
 已加入下列屬性至 <xref:System.Reflection> 命名空間來識別類型、方法或欄位是否為 `SecurityCritical`、`SecuritySafeCritical`，或 `SecurityTransparent`：<xref:System.Type.IsSecurityCritical%2A>、<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> 和 <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>。 您可以使用這些屬性來判斷透明度，方法是使用反映，而非檢查屬性是否存在。 透明度規則很複雜，而且檢查屬性是否存在可能不足夠。  
  
> [!NOTE]
>  A`SafeCritical`方法會傳回`true`兩者<xref:System.Type.IsSecurityCritical%2A>和<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>，因為`SafeCritical`確實相當重要 （其相同的功能與關鍵程式碼，不過它可以從透明程式碼呼叫）。  
  
 動態方法會繼承它們所附加之目標模組的透明度，但是不會繼承類型的透明度 (如果它們附加至類型的話)。  
  
### <a name="skip-verification-in-full-trust"></a>在完全信任中略過驗證  
 若為完全信任的透明組件，您就可以在 <xref:System.Security.SecurityRulesAttribute> 屬性中，將 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> 屬性設定為 `true`，藉以略過驗證：  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> 屬性預設為 `false`，因此這個屬性必須設定為 `true`，才能略過驗證。 您應該僅針對最佳化目的進行此作業。 您應該確認使用的組件中的透明程式碼是否可驗證`transparent`選項[PEVerify 工具](../../../docs/framework/tools/peverify-exe-peverify-tool.md)。  
  
## <a name="see-also"></a>另請參閱  
 [安全性透明的程式碼，層級 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [安全性變更](../../../docs/framework/security/security-changes.md)
