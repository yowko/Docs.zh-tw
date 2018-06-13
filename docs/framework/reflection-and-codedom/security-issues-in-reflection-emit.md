---
title: 反映發出中的安全性問題
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- emitting dynamic assemblies, security
- reflection emit, security
- reflection emit, partial trust scenarios
- partial trust,emitting dynamic methods
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- dynamic assemblies, security
ms.assetid: 0f8bf8fa-b993-478f-87ab-1a1a7976d298
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57db77b64ddcbe282fed035b52bb122901383ca4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398868"
---
# <a name="security-issues-in-reflection-emit"></a>反映發出中的安全性問題
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供三種發出 Microsoft 中繼語言 (MSIL) 的方式，每種都有它自己的安全性問題：  
  
-   [動態組件](#Dynamic_Assemblies)  
  
-   [匿名裝載的動態方法](#Anonymously_Hosted_Dynamic_Methods)  
  
-   [與現有組件建立關聯的動態方法](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 無論您產生動態程式碼的方式為何，執行產生的程式碼需要所有權限，這些是產生的程式碼所使用之類型和方法所需的。  
  
> [!NOTE]
>  反映在程式碼上以及發出程式碼所需的權限已在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的後續發行中變更。 請參閱本主題稍後的[版本資訊](#Version_Information)。  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>動態組件  
 使用 <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> 方法的多載來建立動態組件。 由於刪除全機器安全性原則，這個方法的大部分多載已在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中遭取代。 (請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。)無論信任層級為何，剩餘的多載可由任何程式碼執行。 這些多載可分為兩個群組：當建立動態組件時，指定要套用至動態組件的屬性清單，以及不套用至動態組件的屬性清單。 當您建立組件時，如果您未套用 <xref:System.Security.SecurityRulesAttribute> 屬性來指定組件的透明度模型，則透明度模型會繼承自發出的組件。  
  
> [!NOTE]
>  動態組件建立後，使用 <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> 方法套用至動態組件的屬性並不會生效，直到組件已儲存至磁碟並再次載入記憶體中。  
  
 動態組件中的程式碼可以存取可見的類型和其他組件中的成員。  
  
> [!NOTE]
>  動態組件不使用允許存取非公用類型和成員之動態方法的 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 和 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標。  
  
 暫時性動態組件會在記憶體中建立，並永遠不會儲存到磁碟，所以它們不需要檔案存取權限。 儲存動態組件至磁碟需要具有適當旗標的 <xref:System.Security.Permissions.FileIOPermission>。  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>從部分信任的程式碼產生動態組件  
 請考慮具有網際網路權限的組件可產生暫時性動態組件並執行其程式碼的條件：  
  
-   動態組件只會使用公用類型和其他組件的成員。  
  
-   在部分信任組件的授權集中包含這些類型和成員所要求的權限。  
  
-   該組件不會儲存到磁碟。  
  
-   不會產生偵錯符號。 (`Internet` 和 `LocalIntranet` 權限集合不包含必要的權限。)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>匿名裝載的動態方法  
 匿名裝載的動態方法可用兩個 <xref:System.Reflection.Emit.DynamicMethod> 建構函式建立，該函式並未指定相關聯的類型或模組、<xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> 和 <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>。 這些建構函式會將動態方法置於系統提供、完全受信任的安全性透明組件中。 使用這些建構函式，或發出動態方法的程式碼不需要權限。  
  
 相反地，當建立匿名裝載的動態方法時，會擷取呼叫堆疊。 當建構方法時，會對已擷取的呼叫堆疊提出安全性要求。  
  
> [!NOTE]
>  就觀念上而言，會在方法建構期間提出要求。 也就是當發出每個 MSIL 指示時，可提出要求。 在目前的實作中，當 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> 方法被呼叫，或是當 Just-In-Time (JIT) 編譯器被叫用時，如果此方法被叫用卻沒有呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>，就會提出所有的要求。  
  
 如果應用程式定義域允許，則匿名裝載的動態方法可以跳過 JIT 可見度檢查，且受下列限制：由匿名裝載的動態方法存取的非公用類型和成員必須位於組件中，且該組件的授權集與發出呼叫堆疊的授權集相等，或是為其子集。 如果應用程式定義域對 <xref:System.Security.Permissions.ReflectionPermission> 授與 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標，則會啟用這項跳過 JIT 可見度檢查的限制功能。  
  
-   如果您的方法只使用公用類型和成員，則在建構期間不需要權限。  
  
-   如果您指定 JIT 可見度檢查應該要跳過，則在建構方法時提出的要求會包含具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>以及包含正在存取非公用成員之組件的授權集。  
  
 因為非公用成員的授權集已納入考慮，所以已授與 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 的部分信任程式碼無法藉由執行受信任組件的非公用成員來提高權限。  
  
 與任何其他發出程式碼一樣，執行動態方法需要動態方法所使用之方法要求的任何權限。  
  
 裝載匿名裝載動態方法的系統組件會使用 <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> 透明度模型，這是在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之前的 .NET Framework 中所使用的透明度模型 。  
  
 如需詳細資訊，請參閱 <xref:System.Reflection.Emit.DynamicMethod> 類別。  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>從部分信任的程式碼產生匿名裝載的動態方法  
 請考慮具有網際網路權限的組件可產生匿名裝載的動態方法並予以執行的條件：  
  
-   動態方法只會使用公用類型和成員。 如果其授權集包含 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>，則它可以使用授權集為發出組件授權集子集或與其相等的任何組件之非公用類型與成員。  
  
-   部分信任組件的授權集包含動態方法所使用的所有類型及成員所需的權限。  
  
> [!NOTE]
>  動態方法並不支援偵錯符號。  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>與現有組件相關聯的動態方法  
 若要將動態方法和現有組件中的類型或模組相關聯，請使用任何一種指定相關聯的類型或模組的 <xref:System.Reflection.Emit.DynamicMethod> 建構函式。 呼叫這些建構函式所需的權限有所不同，因為將動態方法與現有類型或模組產生關聯會讓動態方法存取非公用類型和成員：  
  
-   與類型相關聯的動態方法可以存取所有該類型的成員，甚至是私用成員，且能存取包含相關聯的類型之組件中的所有內部類型和成員。  
  
-   與模組相關聯的動態方法可存取模組中所有 `internal` 類型和成員 (在 Visual Basic 中為 `Friend`，在 Common Language Runtime 中繼資料中為 `assembly`)。  
  
 此外，您可以使用會指定略過 JIT 編譯器可見度檢查能力的建構函式。 這樣可讓您的動態方法在所有組件中存取所有類型和成員，不論存取層級為何。  
  
 建構函式所要求的權限取決於您決定要授與動態方法多少的存取權：  
  
-   如果您的方法只使用公用類型和成員，而且您將它和您自己的類型或模組產生關聯，則不需要任何權限。  
  
-   如果您指定應該略過 JIT 可見度檢查，則建構函式會要求具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>。  
  
-   如果您將動態方法與其他類型產生關聯，甚至是在您自己的組件中的另一個類型，則建構函式會要求具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 和具有 <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.SecurityPermission>。  
  
-   如果您將動態方法和其他組件中的類型或模組產生關聯，則建構函式會要求兩項事物：具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 及包含其他模組之組件的授權集。 也就是您的呼叫堆疊必須包含所有在目標模組授權集中的權限，加上 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>。  
  
    > [!NOTE]
    >  為了回溯相容性，如果目標授權集加上 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 的要求失敗，則建構函式會要求具有 <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.SecurityPermission>。  
  
 雖然這份清單中的項目係依據發出的組件之授權集而描述，請記得這會對完整呼叫堆疊提出需求，包含應用程式定義域界限。  
  
 如需詳細資訊，請參閱 <xref:System.Reflection.Emit.DynamicMethod> 類別。  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>從部分信任的程式碼產生動態方法  
  
> [!NOTE]
>  從部分信任的程式碼產生動態方法的建議方式是使用[匿名裝載的動態方法](#Anonymously_Hosted_Dynamic_Methods)。  
  
 請考慮具有網際網路權限的組件可產生動態方法並予以執行的條件：  
  
-   與動態方法發出的模組或類型相關聯的動態方法，或是其授權集會包含 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>，且這會與組件中的模組相關聯，該組件的授權集為發出組件授權集子集或與其相等。  
  
-   動態方法只會使用公用類型和成員。 如果其授權集包含 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>，而且與組件中的模組相關聯，該組件的授權集為發出組件授權集子集或與其相等，則它可以在相關聯的模組中使用標示為 `internal` 的類型和成員 (在 Visual Basic 中為 `Friend`，在 Common Language Runtime 中繼資料中為 `assembly`)。  
  
-   部分信任組件的授權集包含動態方法所使用的所有類型及成員所要求的權限。  
  
-   該動態方法不會略過 JIT 可見度檢查。  
  
> [!NOTE]
>  動態方法並不支援偵錯符號。  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>版本資訊  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，淘汰全機器的安全性原則，且安全性透明度變成預設強制機制。 請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。  
  
 從 [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] 開始，當發出動態組件和動態方法時，不再需要具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>。 在所有舊版 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中需要此旗標。  
  
> [!NOTE]
>  根據預設，具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 包含在 `FullTrust` 和 `LocalIntranet` 具名權限集合，而不是 `Internet` 權限集合。 因此，在舊版的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中，僅當程式庫執行針對 <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit> 的 <xref:System.Security.PermissionSet.Assert%2A> 時，程式庫才可搭配網際網路權限使用。 這類程式庫需要仔細的安全性檢閱，因為編碼錯誤可能會造成安全性漏洞。 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 允許在部分信任案例中發出程式碼，而不需提出任何安全性要求，因為產生的程式碼本質上並非有權限的作業。 也就是產生的程式碼之權限不會比發出程式碼的組件還多。 這可讓程式庫發出安全性透明的程式碼，並可免除 <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit> 判斷提示的需要，這可簡化撰寫安全程式庫的工作。  
  
 此外，[!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 導入了 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> 旗標，用來從部分信任的動態方法中存取非公用類型和成員。 對於會存取非公用類型和成員的動態方法，舊版的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 需要 <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> 旗標；這是永遠不該授與部分信任程式碼的權限。  
  
 最後，[!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 導入了匿名裝載的方法。  
  
### <a name="obtaining-information-on-types-and-members"></a>取得類型和成員資訊  
 從 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 開始，取得非公用類型和成員的相關資訊不需要權限。 反映會用來取得發出動態方法需要的資訊。 例如，<xref:System.Reflection.MethodInfo> 物件會用來發出方法呼叫。 舊版的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 需要具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>。 如需詳細資訊，請參閱[反映的安全性考量](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)。  
  
## <a name="see-also"></a>請參閱  
 [反映的安全性考量](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)  
 [發出動態方法和組件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)
