---
title: "逐步解說：在部分信任案例中發出程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "匿名裝載的動態方法 [.NET Framework]"
  - "動態方法"
  - "發出動態組件, 部分信任案例"
  - "部分信任, 發出動態方法"
  - "部分信任, 反映"
  - "反映發出, 匿名裝載的動態方法"
  - "反映發出, 動態方法"
  - "反映發出, 部分信任案例"
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 逐步解說：在部分信任案例中發出程式碼
反映發出在完全或部分信任都使用相同的 API 集，但部分功能在部分信任的程式碼中需要特殊的使用權限。  此外，反映發出具有匿名裝載動態方法，這項功能是設計與部分信任搭配使用，以供安全性透明的組件使用。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]以前的版本中，發出程式碼需要具有 <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> 旗標的 <xref:System.Security.Permissions.ReflectionPermission>。  此權限預設包含在 `FullTrust` 和 `Intranet` 具名使用權限集合中，但不在 `Internet` 使用權限集合中。  因此，才有 <xref:System.Security.SecurityCriticalAttribute> 屬性同時執行的 <xref:System.Security.Permissions.ReflectionPermissionFlag>，則 <xref:System.Security.PermissionSet.Assert%2A> 方法程式庫可以從部分信任使用。  這類程式庫需要經審慎的安全性檢閱，因為程式碼錯誤可能會產生安全性漏洞。  [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 允許程式碼在部分信任案例中發出，而且不發出任何安全性要求，因為產生程式碼本身並非特殊權限操作。  也就是說，產生的程式碼不會有比發出它的組件更大的使用權限。  這可讓發出程式碼的程式庫成為安全性透明，而無須判斷提示 \(Assert\) <xref:System.Security.Permissions.ReflectionPermissionFlag>，因此撰寫安全的程式庫就不需要如此審慎的安全性檢閱。  
  
 這個逐步解說將說明下列工作：  
  
-   [設定簡單沙箱來測試部分信任的程式碼](#Setting_up)。  
  
    > [!IMPORTANT]
    >  這是在部分信任中實驗程式碼的簡單方式。  若要執行實際來自未受信任位置的程式碼，請參閱 [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)。  
  
-   [在部分信任應用程式定義域中執行程式碼](#Running_code)  
  
-   [使用匿名裝載動態方法，在部分信任中發出和執行程式碼](#Using_methods)  
  
 如需在部分信任案例中發出程式碼的詳細資訊，請參閱[反映發出中的安全性問題](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)。  
  
 如需這些程序所示範的程式碼完整清單，請參閱本逐步解說最後的[範例](#Example)一節。  
  
<a name="Setting_up"></a>   
## 設定部分信任位置  
 下列兩個程序說明如何設定位置，讓您可以使用部分信任來測試程式碼。  
  
-   第一個程序說明如何建立沙箱應用程式定義域，讓程式碼獲得網際網路使用權限。  
  
-   第二個程序說明如何將具有 <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 加入至部分信任的應用程式定義域，以便存取具有相同或更低信任權限的組件中的私用資料。  
  
### 建立沙箱應用程式定義域  
 若要建立應用程式定義域，讓組件以部分信任權限執行，您必須使用 [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> 方法多載建立應用程式定義域，指定要授與組件的使用權限集合。  指定授權集最簡單的方式就是從安全性原則擷取具名使用權限集合。  
  
 下列程序會建立沙箱應用程式定義域，在其中以部分信任權限執行您的程式碼，以測試發出的程式碼只能存取公用型別之公用成員的案例。  緊接在後面的程序會說明如何加入 <xref:System.Security.Permissions.ReflectionPermissionFlag>，以測試發出的程式碼可存取授與相同或更低使用權限的組件中之非公用型別和成員的案例。  
  
##### 若要建立部分信任的應用程式定義域  
  
1.  建立要授與沙箱應用程式定義域中之組件的使用權限集合。  在此例中，會使用網際網路區域的使用權限集合。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2.  建立 <xref:System.AppDomainSetup> 物件，以應用程式路徑初始化應用程式定義域。  
  
    > [!IMPORTANT]
    >  為了容易說明，這個程式碼範例會使用目前的資料夾。  若要執行實際來自網際網路的程式碼，請針對未受信任的程式碼使用個別的資料夾，如 [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)中所述。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3.  建立應用程式定義域，並針對在應用程式定義域中執行的所有組件指定應用程式定義域安裝資訊以及授權集。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> 方法多載的最後一個參數可讓您指定授與完全信任的組件集合，而非應用程式定義域的授權集。  您不需要指定應用程式使用的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件，因為這些組件位於全域組件快取中。  全域組件快取中的組件永遠是完全信任的。  您可以使用此參數指定不在全域組件快取中的強式名稱組件。  
  
### 加入 RestrictedMemberAccess 至沙箱化定義域  
 主應用程式可允許匿名裝載動態方法存取信任層級與發出程式碼之組件相同或更低的組件中的私用資料。  為了讓此限制能力略過 Just\-In\-Time \(JIT\) 可視性檢查，主應用程式會將具有 <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> \(RMA\) 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 物件加入到授權集。  
  
 例如，主應用程式可能會將網際網路使用權限加上 RMA 授與網際網路應用程式，讓網際網路應用程式發出存取其本身組件內私用資料的程式碼。  由於存取限於有相同或更低信任權限的組件，網際網路應用程式無法存取完全信任組件 \(如 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件\) 的成員。  
  
> [!NOTE]
>  為防止權限升級，當建構匿名裝載動態方法時，會包含發出組件的堆疊資訊。  當叫用方法時，就會檢查堆疊資訊。  如此一來，從完全信任程式碼叫用的匿名裝載動態方法，仍會限制在發出組件的信任層級。  
  
##### 若要建立部分信任加上 RMA 的應用程式定義域  
  
1.  建立具有 <xref:System.Security.Permissions.ReflectionPermissionFlag> \(RMA\) 旗標的新 <xref:System.Security.Permissions.ReflectionPermission> 物件，然後使用 <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=fullName> 方法將該使用權限加入到授權集。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     如果授權集還沒有該使用權限，<xref:System.Security.PermissionSet.AddPermission%2A> 方法會加入使用權限。  如果權限集已包含該使用權限，則會將指定的旗標加入到現有的使用權限。  
  
    > [!NOTE]
    >  RMA 是匿名裝載動態方法的功能。  當一般動態方法略過 JIT 可視性檢查時，發出的程式碼就需要完全信任。  
  
2.  建立應用程式定義域，並指定應用程式定義域安裝資訊以及授權集。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## 在沙箱應用程式定義域中執行程式碼  
 下列程序說明如何使用可在應用程式定義域中執行的方法定義類別、如何在定義域中建立類別的執行個體，以及如何執行其方法。  
  
#### 若要在應用程式定義域中定義和執行方法  
  
1.  定義從 <xref:System.MarshalByRefObject> 衍生的類別  這可讓您在其他應用程式定義域中建立類別的執行個體，以及跨應用程式定義域界限呼叫方法。  在這個範例中，此類別命名為 `Worker`。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2.  定義公用方法，其中包含要執行的程式碼。  在這個範例中，程式碼會發出簡單的動態方法、建立委派來執行方法，並叫用委派。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3.  在主程式中，取得組件的顯示名稱。  當您在沙箱應用程式定義域中建立 `Worker` 類別的執行個體時，會用到這個名稱。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4.  在主程式中，建立沙箱應用程式定義域，如本逐步解說的[第一個程序](#Setting_up)所述。  您不需要在 `Internet` 使用權限集合加入任何使用權限，因為 `SimpleEmitDemo` 方法只使用公用方法。  
  
5.  在主程式中，於沙箱應用程式定義域中建立 `Worker` 類別的執行個體。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> 方法會在目標應用程式定義域中建立物件，並傳回可用來呼叫物件屬性和方法的 Proxy。  
  
    > [!NOTE]
    >  如果您在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]中使用這段程式碼，必須變更類別的名稱 \(包括命名空間\)。  依預設，命名空間是專案的名稱。  例如，如果專案是 "PartialTrust"，類別名稱就必須是 "PartialTrust.Worker"。  
  
6.  加入呼叫 `SimpleEmitDemo` 方法的程式碼。  此呼叫會跨應用程式定義域界限封送處理，而程式碼會在沙箱應用程式定義域中執行。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## 使用匿名裝載動態方法  
 匿名裝載動態方法與系統提供的透明組件相關聯。  因此，它們所包含的程式碼也是透明的。  另一方面，一般動態方法必須與現有的模組 \(不論是直接指定還是根據相關的型別推斷\) 相關聯，並且從該模組中取得其安全性層級。  
  
> [!NOTE]
>  要使動態方法與提供匿名裝載的組件產生關聯，唯一方法就是使用下列程序所述的建構函式 \(Constructor\)。  您不能明確指定匿名裝載組件中的模組。  
  
 一般動態方法可以存取與其相關聯之模組的內部成員，或相關聯型別的私用成員。  由於匿名裝載動態方法與其他程式碼分開，就無法存取私用資料。  不過，這些方法可在受限的情況下略過 JIT 可視性檢查，藉此存取私用資料。  這限於信任層級與發出程式碼之組件相同或更低的組件。  
  
 為防止權限升級，當建構匿名裝載動態方法時，會包含發出組件的堆疊資訊。  當叫用方法時，就會檢查堆疊資訊。  從完全信任程式碼叫用的匿名裝載動態方法，仍會限制在發出它之組件的信任層級。  
  
#### 若要使用匿名裝載動態方法  
  
-   使用沒有指定相關聯模組或型別的建構函式，建立匿名裝載動態方法。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     如果匿名裝載動態方法只使用公用型別和方法，就不需要限制成員存取，也不需要略過 JIT 可視性檢查。  
  
     發出動態方法並不需要特殊使用權限，不過，發出的程式碼需要其使用的型別和方法所需的使用權限。  例如，如果發出的程式碼呼叫存取檔案的方法，就需要 <xref:System.Security.Permissions.FileIOPermission>。  如果信任層級未包含該使用權限，則執行發出的程式碼時，會擲回安全性例外狀況。  此處顯示的程式碼會發出只使用 <xref:System.Console.WriteLine%2A?displayProperty=fullName> 方法的動態方法。  因此，程式碼可以從部分信任的位置執行。  
  
-   或者，使用 [DynamicMethod\(String, Type, Type\<xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> 建構函式並將 `restrictedSkipVisibility` 參數指定為 `true`，來建立能在受限情況下略過 JIT 可視性檢查的匿名裝載動態方法。  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     限制在於，此匿名裝載動態方法只能存取信任層級與發出組件相同或更低的組件中的私用資料。  例如，如果動態方法使用網際網路信任權限執行，它就可以存取其他也使用網際網路信任權限執行之組件中的私用資料，但無法存取 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件的私用資料。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件會安裝在全域組件快取中，而且永遠是完全信任的。  
  
     匿名裝載動態方法只有在主應用程式授與具有 <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> 旗標的 <xref:System.Security.Permissions.ReflectionPermission> 時，才能使用此限制能力略過 JIT 可視性檢查。  當叫用方法時，就會要求此使用權限。  
  
    > [!NOTE]
    >  當建構動態方法時，會包含發出組件的呼叫堆疊資訊。  因此，會對發出組件要求使用權限，而不是叫用方法的組件。  這樣可以防止發出的程式碼以升級使用權限執行。  
  
     本逐步解說最後的[完整程式碼範例](#Example)示範限制成員存取的用法與限制。  其中的 `Worker` 類別包含可建立匿名裝載動態方法的方法，不論匿名裝載動態方法是否能在受限情況下略過可視性檢查，而且範例也顯示在具有不同信任層級的應用程式定義域中執行此方法的結果。  
  
    > [!NOTE]
    >  在受限情況下略過可視性檢查，是匿名裝載動態方法的一項功能。  當一般動態方法略過 JIT 可視性檢查時，它們必須被授與完全信任。  
  
<a name="Example"></a>   
## 範例  
  
### 描述  
 下列程式碼範例示範 <xref:System.Security.Permissions.ReflectionPermissionFlag> 旗標的用法，其允許匿名裝載動態方法略過 JIT 可視性檢查，但目標成員的信任層級必須與發出程式碼的組件相同或更低。  
  
 這個範例定義了一個 `Worker` 類別，此類別可跨應用程式定義域界限封送處理。  此類別有兩個發出和執行動態方法的 `AccessPrivateMethod` 方法多載。  第一個多載會發出動態方法來呼叫 `Worker` 類別的私用 `PrivateMethod` 方法，而且可發出具有或沒有 JIT 可視性檢查的動態方法。  第二個多載會發出動態方法來存取 <xref:System.String> 類別的 `internal` 屬性 \(在 Visual Basic 為 `Friend` 屬性\)。  
  
 這個範例會使用 Helper 方法來建立限制為 `Internet` 使用權限的授權集，然後建立應用程式定義域，方式是使用 [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> 方法多載指定在該定義域中執行的所有程式碼都使用此授權集。  這個範例會在應用程式定義域中建立 `Worker` 類別的執行個體，然後執行 `AccessPrivateMethod` 方法兩次。  
  
-   `AccessPrivateMethod` 方法第一次執行時，會強制執行 JIT 可視性檢查。  動態方法在叫用時會失敗，因為 JIT 可視性檢查使其無法存取私用方法。  
  
-   `AccessPrivateMethod` 方法第二次執行時，會略過 JIT 可視性檢查。  動態方法在編譯時會失敗，因為 `Internet` 授權集沒有授與足夠的使用權限來略過可視性檢查。  
  
 此範例會將具有 <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> 的 <xref:System.Security.Permissions.ReflectionPermission> 加入至授權集。  範例接著會建立第二個定義域，指定將新授權集中的使用權限授與該定義域中執行的所有程式碼。  這個範例會在新的應用程式定義域中建立 `Worker` 類別的執行個體，然後執行 `AccessPrivateMethod` 方法的兩個多載。  
  
-   `AccessPrivateMethod` 方法的第一個多載會執行，並略過 JIT 可視性檢查。  動態方法將成功編譯和執行，因為發出程式碼的組件與包含私用方法的組件是同一個。  因此，信任層級是相同的。  如果包含 `Worker` 類別的應用程式有數個組件，則無論是哪一個組件，上述程序都會成功，因為這些組件都位於相同的信任層級。  
  
-   `AccessPrivateMethod` 方法的第二個多載會執行，並再次略過 JIT 可視性檢查。  這次動態方法在編譯時會失敗，因為它會嘗試存取 <xref:System.String> 類別的 `internal` `FirstChar` 屬性。  包含 <xref:System.String> 類別的組件是完全受信任的。  因此，它的信任層級比發出程式碼的組件高。  
  
 這項比較顯示 <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> 如何讓部分信任的程式碼略過其他部分信任程式碼的可視性檢查，而不會破壞受信任程式碼的安全性。  
  
### 程式碼  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## 編譯程式碼  
  
-   如果您在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中建置這個程式碼範例，必須變更類別的名稱，以加入傳遞到 <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> 方法的命名空間。  依預設，命名空間是專案的名稱。  例如，如果專案是 "PartialTrust"，類別名稱就必須是 "PartialTrust.Worker"。  
  
## 請參閱  
 [反映發出中的安全性問題](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)   
 [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)