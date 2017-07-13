---
title: "逐步解說：在部分信任案例中發出程式碼 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit, anonymously hosted dynamic methods
- partial trust, reflection
- partial trust, emitting dynamic methods
- reflection emit, partial trust scenarios
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6f3dc4235c75d7438f019838cb22192f4dc7c41a
ms.openlocfilehash: 73618a140daa4146f80472872a54884b7032da9a
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

---
<a id="walkthrough-emitting-code-in-partial-trust-scenarios" class="xliff"></a>

# 逐步解說：在部分信任案例中發出程式碼
反映發出在完整或部分信任中使用相同的 API 集合，但在部分信任程式碼中，有些功能需要特殊權限。 此外，反映發出還有一項匿名裝載動態方法的功能，設計搭配部分信任使用並可供安全性透明組件使用。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] 之前，發出程式碼需要 <xref:System.Security.Permissions.ReflectionPermission> 及 <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=fullName> 旗標。 根據預設，此權限包含在 `FullTrust` 和 `Intranet` 具名權限集合中，不在 `Internet` 權限集合中。 因此，只有在程式庫有 <xref:System.Security.SecurityCriticalAttribute> 屬性，同時執行了 <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit> 的 <xref:System.Security.PermissionSet.Assert%2A> 方法，才能從部分信任使用該程式庫。 這類程式庫需要仔細的安全性檢閱，因為編碼錯誤可能會造成安全性漏洞。 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 允許在部分信任案例中發出程式碼，而不需提出任何安全性要求，因為產生的程式碼本質上並非有權限的作業。 也就是產生的程式碼之權限不會比發出程式碼的組件還多。 這可讓發出程式碼的程式庫成為安全性透明的，並移除判斷提示 <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit> 的需要，讓撰寫安全的程式庫不需要仔細的安全性檢閱。  
  
 這個逐步解說將說明下列工作：  
  
-   [設定簡單沙箱以測試部分信任程式碼](#Setting_up)。  
  
    > [!IMPORTANT]
    >  這是實驗部分信任程式碼的簡單方法。 若要執行實際來自不受信任位置的程式碼，請參閱[如何：在沙箱中執行部分信任的程式碼](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)。  
  
-   [在部分信任的應用程式定義域中執行程式碼](#Running_code)。  
  
-   [使用匿名裝載的動態方法，發出並執行部分信任的程式碼](#Using_methods)。  
  
 如需在部分信任案例中發出程式碼的詳細資訊，請參閱[反映發出中的安全性問題](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)。  
  
 如需這些程序所示範程式碼的完整清單，請參閱本逐步解說結尾的[範例](#Example)一節。  
  
<a name="Setting_up"></a>   
<a id="setting-up-partially-trusted-locations" class="xliff"></a>

## 設定部分信任的位置  
 下列兩項程序會示範如何從您可以測試部分信任程式碼的位置設定位置。  
  
-   第一項程序示範如何建立沙箱應用程式定義域，程式碼在其中會獲授與網際網路權限。  
  
-   第二項程序顯示如何將有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=fullName> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>，新增至部分信任的應用程式定義域，以便存取相同或較低信任組件中的私用資料。  
  
<a id="creating-sandboxed-application-domains" class="xliff"></a>

### 建立沙箱應用程式定義域  
 若要建立可用部分信任執行組件的應用程式定義域，您必須使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> 方法多載來建立應用程式定義域，指定將權限集授與這些組件。 指定授權集最簡單的方式，是從安全性原則擷取具名權限集。  
  
 下列程序會建立沙箱應用程式定義域，用部分信任的執行程式碼，測試發出的程式碼只能存取公用類型公用成員的案例。 後續程序示範如何新增 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>，測試發出的程式碼可以存取非公用類型和成員的案例，而這些類型和成員所在組件具有相同或較低的權限。  
  
<a id="to-create-an-application-domain-with-partial-trust" class="xliff"></a>

##### 建立部份信任的應用程式定義域  
  
1.  建立權限集，以授與沙箱應用程式定義域中的組件。 在此情況下，會使用網際網路區域的權限集。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]  [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2.  建立 <xref:System.AppDomainSetup> 物件來初始化具有應用程式路徑的應用程式定義域。  
  
    > [!IMPORTANT]
    >  為簡單起見，此程式碼範例會使用目前的資料夾。 若要執行實際來自網際網路的程式碼，不受信任的程式碼請使用另外的資料夾，依[如何：在沙箱中執行部分信任的程式碼](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)中所述。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]  [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3.  建立應用程式定義域，指定應用程式定義域安裝資訊，以及在應用程式定義域中執行的所有組件授權集。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]  [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> 方法多載的最後一個參數可讓您指定組件集合，授與完全信任，而不是應用程式定義域的授權集。 因為這些組件位於全域組件快取，所以您不必指定應用程式使用的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件。 全域組件快取中的組件一律為完全信任。 您可以使用這個參數指定不在全域組件快取中的強式名稱組件。  
  
<a id="adding-restrictedmemberaccess-to-sandboxed-domains" class="xliff"></a>

### 將 RestrictedMemberAccess 新增至沙箱定義域  
 主應用程式可以允許匿名裝載的動態方法，存取組件中的私用資料，這些組件的信任層級都等於或低於發出程式碼的組件信任層級。 若要啟用此有限功能以略過 Just-In-Time (JIT) 可視性檢查，主應用程式會將具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=fullName> (RMA) 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 物件新增至授權集。  
  
 例如，主機可能會授與網際網路應用程式加上 RMA 的網際網路權限，讓網際網路應用程式可以發出程式碼，存取自己組件中的私用資料。 因為限制存取相同或較低信任的組件，所以網際網路應用程式無法存取完全信任組件的成員，例如 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件。  
  
> [!NOTE]
>  為防止提高權限，建構匿名裝載的動態方法時，會包含發出組件的堆疊資訊。 叫用方法時會檢查堆疊資訊。 因此，從完全信任程式碼叫用的匿名裝載動態方法，其信任層級仍限於發出組件的信任層級。  
  
<a id="to-create-an-application-domain-with-partial-trust-plus-rma" class="xliff"></a>

##### 建立加上 RMA 的部份信任應用程式定義域  
  
1.  建立具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>(RMA) 旗標的新 <xref:System.Security.Permissions.ReflectionPermission> 物件，並使用 <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=fullName> 方法將權限新增至授權集。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]  [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     權限若未包含在內，<xref:System.Security.PermissionSet.AddPermission%2A> 方法會將權限新增至授權集。 如果授權集已包含權限，指定的旗標就會新增至現有的權限。  
  
    > [!NOTE]
    >  RMA 是匿名裝載動態方法的功能。 當一般的動態方法略過 JIT 可見度檢查時，發出的程式碼需要完全信任。  
  
2.  建立應用程式定義域，指定應用程式定義域安裝資訊及授權集。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]  [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
<a id="running-code-in-sandboxed-application-domains" class="xliff"></a>

## 在沙箱應用程式定義域中執行程式碼  
 下列程序說明如何使用可在應用程式定義域中執行的方法來定義類別、如何在定義域中建立類別的執行個體，以及如何執行其方法。  
  
<a id="to-define-and-execute-a-method-in-an-application-domain" class="xliff"></a>

#### 在應用程式定義域中定義及執行方法  
  
1.  定義衍生自 <xref:System.MarshalByRefObject> 的類別。 這可讓您在其他的應用程式定義域中建立類別的執行個體，以及跨應用程式定義域界限進行方法呼叫。 本例中的類別名為 `Worker`。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]  [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2.  定義公用方法，包含您想要執行的程式碼。 在此範例中，程式碼會發出簡單的動態方法、建立委派來執行方法，並叫用委派。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]  [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3.  在您的主程式中，取得組件的顯示名稱。 當您在沙箱應用程式定義域中建立 `Worker` 類別的執行個體時，會使用此名稱。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]  [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4.  在您的主程式中建立沙箱應用程式定義域，如本逐步解說的[第一項程序](#Setting_up)中所述。 因為 `SimpleEmitDemo` 方法只使用公用方法，所以您不必新增任何權限到 `Internet` 權限集。  
  
5.  在您的主程式中，在沙箱應用程式定義域中建立 `Worker` 類別的執行個體。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]  [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> 方法會在目標應用程式定義域中建立物件，傳回可以用來呼叫物件屬性和方法的 proxy。  
  
    > [!NOTE]
    >  如果您在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中使用這段程式碼，則必須變更類別名稱以包含命名空間。 命名空間是專案的預設名稱。 例如，如果專案是 "PartialTrust"，則類別名稱必須是 "PartialTrust.Worker"。  
  
6.  新增程式碼以呼叫 `SimpleEmitDemo` 方法。 呼叫會跨應用程式定義域界限封送處理，而程式碼則在沙箱應用程式定義域中執行。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]  [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
<a id="using-anonymously-hosted-dynamic-methods" class="xliff"></a>

## 使用匿名裝載的動態方法  
 匿名裝載動態方法與系統提供的透明組件相關聯。 因此，它們所包含的程式碼是透明的。 另一方面，一般的動態方法必須與現有的模組相關聯 (不論是直接指定或推斷的相關聯類型)），並接受該模組的安全性層級。  
  
> [!NOTE]
>  動態方法與提供匿名裝載之組件建立關聯的唯一方法，是使用下列程序中描述的建構函式。 您不能在匿名裝載的組件中明確指定模組。  
  
 一般的動態方法可以存取相關聯模組的內部成員，或相關聯類型的私用成員。 因為匿名裝載的動態方法和其他程式碼是分開的，所以它們不能存取私用資料。 但是，它們在有限的情況下可以略過 JIT 可見度檢查，存取私用資料。 這項功能僅限於信任層級等於或低於發出程式碼組件信任層級的組件。  
  
 為防止提高權限，建構匿名裝載的動態方法時，會包含發出組件的堆疊資訊。 叫用方法時會檢查堆疊資訊。 從完全信任程式碼叫用的匿名裝載動態方法，其信任層級仍限於發出組件的信任層級。  
  
<a id="to-use-anonymously-hosted-dynamic-methods" class="xliff"></a>

#### 使用匿名裝載的動態方法  
  
-   使用不指定相關聯模組或類型的建構函式，建立匿名裝載的動態方法。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]  [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     如果匿名裝載的動態方法只使用公用類型和方法，就不需要限制成員存取，也不必略過 JIT 可見度檢查。  
  
     不需要特殊權限也可以發出動態方法，但發出的程式碼需要所用類型和方法要求的權限。 例如，如果發出的程式碼呼叫存取檔案的方法，它需要 <xref:System.Security.Permissions.FileIOPermission>。 如果信任層級不包含該權限，則執行發出的程式碼時，會擲回安全性例外狀況。 這裡顯示的程式碼會發出只使用 <xref:System.Console.WriteLine%2A?displayProperty=fullName> 方法的動態方法。 因此，程式碼可以從部分信任的位置執行。  
  
-   或者，使用 <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> 建構函式並指定 `restrictedSkipVisibility` 參數的 `true`，建立有限功能的匿名裝載動態方法以略過 JIT 可見度檢查。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]  [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     限制是匿名裝載的動態方法只可以存取信任層級等於或低於發出組件信任層級的組件私用資料。 例如，如果動態方法是以網際網路信任執行，它就可以存取也以網際網路信任執行的其他組件的私用資料，但無法存取 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件的私用資料。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件安裝在全域組件快取中，一律為完全信任。  
  
     只有當主應用程式授權有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=fullName> 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 時，匿名裝載動態方法才可以使用此有限功能略過 JIT 可見度檢查。 叫用方法時才要求此權限。  
  
    > [!NOTE]
    >  建構動態方法時會包含發出組件的呼叫堆疊資訊。 因此，會要求發出組件的權限，而不是叫用方法的組件權限。 這可防止以提高的權限執行發出的程式碼。  
  
     本逐步解說結尾的[完整程式碼範例](#Example)會示範有限成員存取的用法和限制。 其 `Worker` 類別有一方法，可以建立匿名裝載動態方法，有受限或不受限制略過可視性檢查的功能，而此範例會示範在不同信任層級的應用程式定義域中執行此方法的結果。  
  
    > [!NOTE]
    >  有限略過可視性檢查是匿名裝載動態方法的功能。 當一般的動態方法略過 JIT 可見度檢查時，它們必須獲授與完全信任。  
  
<a name="Example"></a>   
<a id="example" class="xliff"></a>

## 範例  
  
<a id="description" class="xliff"></a>

### 描述  
 下列程式碼範例示範如何使用 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> 旗標允許匿名裝載動態方法略過 JIT 可見度檢查，但僅限於所在信任層級與發出程式碼的組件信任層級相同或較低的目標成員。  
  
 此範例會定義 `Worker` 類別，可跨應用程式定義域界限封送處理。 此類別有兩個 `AccessPrivateMethod` 方法多載，可以發出和執行動態方法。 第一個多載會發出動態方法，呼叫 `Worker` 類別的私用 `PrivateMethod`方法，而且可以發出包含或不含 JIT 可見度檢查的動態方法。 第二個多載會發出動態方法，存取 <xref:System.String> 類別的 `internal` 屬性 (Visual Basic 為 `Friend` 屬性)。  
  
 範例會使用協助程式方法來建立限於 `Internet` 權限的授權集，然後使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> 方法多載來指定在使用此授權集的定義域中執行的所有程式碼，建立應用程式定義域。 此範例會在應用程式定義域中建立 `Worker` 類別的執行個體，並執行兩次 `AccessPrivateMethod` 方法。  
  
-   第一次執行 `AccessPrivateMethod` 方法時，會強制執行 JIT 可見度檢查。 因為 JIT 可見度檢查會阻止動態方法存取私用方法，所以叫用動態方法會失敗。  
  
-   第二次執行 `AccessPrivateMethod` 方法時，會略過 JIT 可見度檢查。 因為 `Internet` 授權集未授與足夠的權限以略過可見性檢查，所以動態方法在編譯時失敗。  
  
 此範例會將具有 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=fullName> 的 <xref:System.Security.Permissions.ReflectionPermission> 新增至授權集。 然後，此範例會建立第二個定義域，指定將新授權集的權限授與在定義域中執行的所有程式碼。 此範例會在新的應用程式定義域中建立 `Worker` 類別的執行個體，並執行 `AccessPrivateMethod` 方法的兩個多載。  
  
-   執行 `AccessPrivateMethod` 方法的第一個多載，並略過 JIT 可見度檢查。 動態方法成功編譯並執行，因為發出程式碼的組件和包含私用方法的組件相同。 因此，信任層級是相等的。 如果包含 `Worker` 類別的應用程式曾有數個組件，則同樣的程序對這些組件任一個都會成功，因為它們位於相同的信任層級。  
  
-   執行 `AccessPrivateMethod` 方法的第二個多載，再次略過 JIT 可見度檢查。 這次動態方法是在編譯時失敗，因為它會嘗試存取 <xref:System.String> 類別的 `internal` `FirstChar` 屬性。 包含 <xref:System.String> 類別的組件為完全信任。 因此，它的信任層級高於發出程式碼的組件。  
  
 這項比較會示範 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=fullName> 如何啟用部分信任的程式碼，略跳過其他部分信任程式碼的可見度檢查，卻不危及信任程式碼的安全性。  
  
<a id="code" class="xliff"></a>

### 程式碼  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)] [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
<a id="compiling-the-code" class="xliff"></a>

## 編譯程式碼  
  
-   如果您在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中建置此程式碼範例，當您將它傳遞給 <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> 方法時，即必須變更類別名稱以包含命名空間。 命名空間是專案的預設名稱。 例如，如果專案是 "PartialTrust"，則類別名稱必須是 "PartialTrust.Worker"。  
  
<a id="see-also" class="xliff"></a>

## 另請參閱  
 [反映發出中的安全性問題](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)   
 [如何：在沙箱中執行部分信任的程式碼](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
