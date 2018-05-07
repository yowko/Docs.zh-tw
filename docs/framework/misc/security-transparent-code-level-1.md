---
title: 安全性透明的程式碼，層級 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 252611f3aab138ab7344f1afe6eefb0fe2f5ea24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="security-transparent-code-level-1"></a>安全性透明的程式碼，層級 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 透明度可協助開發人員撰寫更安全的 .NET Framework 程式庫，該程式庫會向部分信任的程式碼公開功能。 層級 1 透明度是在 .NET Framework 2.0 版中所引入的，而且主要只在 Microsoft 中使用。 從開始[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用[層級 2 透明度](../../../docs/framework/misc/security-transparent-code-level-2.md)。 不過，層級 1 透明度保留，讓您可以識別必須以舊版安全性規則執行的舊版程式碼。  
  
> [!IMPORTANT]
>  您應該僅針對相容性指定層級 1 透明度；也就是說，您應該僅針對使用 .NET Framework 3.5 或更早版本 (使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 或沒有使用透明度模型) 所開發的程式碼指定層級 1。 例如，對於允許來自部分信任呼叫端 (APTCA) 之呼叫的 .NET Framework 2.0 組件，請使用層級 1 透明度。 對於針對 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 所開發的程式碼，請一律使用層級 2 透明度。  
  
 此主題包括下列章節：  
  
-   [層級 1 透明度模型](#the_level_1_transparency_model)  
  
-   [透明度屬性](#transparency_attributes)  
  
-   [安全性透明度範例](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>層級 1 透明度模型  
 當您使用層級 1 透明度時，就是使用將程式碼分為安全性透明、安全性安全關鍵和安全性關鍵方法的安全性模型。  
  
 您可以將整個組件、組件中的某些類別，或是類別中的某些方法標記為安全性透明。 安全性透明程式碼無法提高權限。 這項限制有三個後果：  
  
-   安全性透明的程式碼無法執行 <xref:System.Security.Permissions.SecurityAction.Assert> 動作。  
  
-   由安全性程式碼所滿足的任何連結要求，都會變成完整的要求。  
  
-   必須在安全性透明程式碼中執行的任何不安全 (無法驗證) 的程式碼，都會導致 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 安全性權限的完整要求。  
  
 這些規則是在執行期間由 Common Language Runtime (CLR) 強制執行。 安全性透明程式碼會將它所回呼的程式碼之所有安全性需求傳遞給呼叫端。 流經安全性透明程式碼的需求，無法提高權限。 如果低度信任的應用程式呼叫安全性透明程式碼，並產生高權限的需求，則此需求會流回低度信任程式碼且失敗。 安全性透明程式碼無法停止此需求，因為它不能執行判斷提示動作。 從完全信任程式碼呼叫的同一個安全性透明程式碼，會產生成功的需求。  
  
 安全性關鍵和安全性透明相反。 安全性關鍵程式碼是以完全信任方式執行，而且可以執行所有需要權限的作業。 安全性安全關鍵程式碼是通過廣泛安全性稽核的特權程式碼，可以確認該程式碼不會允許部分信任的呼叫端使用沒有存取權限的資源。  
  
 您必須明確套用透明度。 處理資料操作與邏輯的大部分程式碼通常可以標記為安全性透明，而執行權限提高的小部分程式碼則可標記為安全性關鍵或安全性安全關鍵。  
  
> [!IMPORTANT]
>  層級 1 透明度受限於組件範圍；這在組件之間沒有強制執行。 層級 1 透明度主要用於 Microsoft 內部進行安全性稽核。 層級 1 組件內的安全性關鍵類型和成員可以由其他組件中的安全性透明程式碼存取。 請務必在所有層級 1 安全性關鍵類型和成員中執行完全信任的連結要求。 安全性安全關鍵類型和成員還必須確認，對於由類型或成員所存取的受保護資源，呼叫端必須擁有權限。  
  
 為了與舊版 .NET Framework 回溯相容，會將所有未以透明度屬性標註的成員視為安全性安全關鍵。 會將所有未標註的類型都視為透明。 沒有任何靜態分析規則可以用來驗證透明度。 因此，您可能需要在執行階段偵錯透明度錯誤。  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>透明度屬性  
 下表說明您可以用來標註程式碼透明度的三個屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|僅在該組件層級受允許。 將該組件中的所有類型和成員都識別為安全性透明。 該組件不能包含任何安全性關鍵程式碼。|  
|<xref:System.Security.SecurityCriticalAttribute>|在無 <xref:System.Security.SecurityCriticalAttribute.Scope%2A> 屬性的組件層級使用時，根據預設，會將組件中的所有程式碼識別為安全性透明，但也表示該組件可能包含安全性關鍵程式碼。<br /><br /> 在類別層級使用時，會將類別或方法識別為安全性關鍵，而不是識別類別的成員。 若要將所有成員都設成安全性關鍵，請將 <xref:System.Security.SecurityCriticalAttribute.Scope%2A> 屬性設為 <xref:System.Security.SecurityCriticalScope.Everything>。 <br /><br /> 在成員層級使用時，該屬性只適用於該成員。<br /><br /> 已識別為安全性關鍵的類別或成員可以執行權限提高。 **重要事項：**層級 1 透明度中安全性關鍵類型和成員的處理為安全性安全關鍵從呼叫外部組件時。 您應該使用完全信任的連結要求來保護安全性關鍵類型和成員，以避免未經授權的權限提高。|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|識別可以由組件中安全性透明程式碼存取的安全性關鍵程式碼。 否則安全性透明程式碼無法存取相同組件中的私用或內部安全性關鍵成員。 這麼做會影響安全性關鍵程式碼，並可能造成非預期的權限提高。 安全性安全關鍵程式碼應該經過嚴密的安全性稽核。 **注意：**安全性安全關鍵類型和成員必須驗證呼叫端的權限，以判斷呼叫端是否具有受保護的資源的存取權限。|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性可以讓安全性透明程式碼存取相同組件中安全性關鍵的成員。 請考慮將組件中的安全性透明及安全性關鍵程式碼區分成兩個組件。 安全性透明程式碼無法查看安全性關鍵程式碼的私用或內部成員。 此外，安全性關鍵程式碼一般是為了存取公用介面而受稽核的。 您可能不希望私用或內部狀態在組件外還能存取；您可能想要讓狀態保持隔離。 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性會維護安全性透明與安全性關鍵程式碼之間的狀態隔離，但是可在必要時提供覆寫隔離的功能。 安全性透明程式碼無法存取私用或內部安全性關鍵程式碼，除非那些成員已經以 <xref:System.Security.SecuritySafeCriticalAttribute> 標記。 套用 <xref:System.Security.SecuritySafeCriticalAttribute> 之前，請先將成員視為已公開並加以稽核。  
  
### <a name="assembly-wide-annotation"></a>組件範圍的註釋  
 下表說明在組件層級中使用安全性屬性的效果。  
  
|Assembly 屬性|組件狀態|  
|------------------------|--------------------|  
|部分信任組件無屬性|所有類型和成員皆為透明的。|  
|在完全信任組件上沒有屬性 (在全域組件快取中或在 `AppDomain` 中識別為完全信任)|所有類型為透明，且所有成員為安全性安全關鍵。|  
|`SecurityTransparent`|所有類型和成員皆為透明的。|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|所有類型和成員皆為安全性關鍵的。|  
|`SecurityCritical`|所有程式碼都預設為透明的。 不過，個別的類型和成員可以有其他屬性。|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>安全性透明度範例  
 若要使用 .NET Framework 2.0 透明度規則 (層級 1 透明度)，請使用下列組件註釋：  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 如果您要使整個組件透明，來表示該組件不含任何關鍵程式碼，而且在任何情況下都不提高權限，則可以使用下列屬性將透明度明確地加入該組件：  
  
```  
[assembly: SecurityTransparent]  
```  
  
 如果您要混合相同組件中的關鍵及透明程式碼，則可以使用 <xref:System.Security.SecurityCriticalAttribute> 屬性標記該組件，表示該組件可以包含關鍵程式碼，如下所示：  
  
```  
[assembly: SecurityCritical]  
```  
  
 如果您要執行安全性關鍵動作，則必須以另一個 <xref:System.Security.SecurityCriticalAttribute> 屬性明確地標記將執行關鍵動作的程式碼，如下列程式碼範例所示：  
  
```  
[assembly: SecurityCritical]  
Public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{      
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 除了 `Critical` 方法 (明確標記為安全性關鍵) 之外，前述程式碼是透明程式碼。 即使有組件層級 <xref:System.Security.SecurityCriticalAttribute> 屬性，透明度仍是預設的設定。  
  
## <a name="see-also"></a>另請參閱  
 [安全性透明的程式碼，層級 2](../../../docs/framework/misc/security-transparent-code-level-2.md)  
 [安全性變更](../../../docs/framework/security/security-changes.md)
