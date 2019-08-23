---
title: 作法：在沙箱中執行部分信任的程式碼
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a439e02046e04d8628415237d6717a74b9922371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910938"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="315b5-102">作法：在沙箱中執行部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="315b5-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="315b5-103">沙箱是指在受限制的安全性環境中執行程式碼的做法，這會限制授與程式碼的存取權限。</span><span class="sxs-lookup"><span data-stu-id="315b5-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="315b5-104">例如，如果您有來自不完全信任來源的 Managed 程式庫，則不應該以完全信任的方式執行。</span><span class="sxs-lookup"><span data-stu-id="315b5-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="315b5-105">相反地，您應該將程式碼放在沙箱，限制其權限為您所預期它會需要的權限 (例如，<xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 權限)。</span><span class="sxs-lookup"><span data-stu-id="315b5-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="315b5-106">您也可以使用沙箱來測試您將散發的程式碼，該程式碼將在部分信任環境中執行。</span><span class="sxs-lookup"><span data-stu-id="315b5-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="315b5-107"><xref:System.AppDomain> 是提供沙箱給 Managed 應用程式的有效方式。</span><span class="sxs-lookup"><span data-stu-id="315b5-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="315b5-108">用來執行部分信任程式碼的應用程式定義域具有權限，於 <xref:System.AppDomain> 中執行時，會定義可以使用的受保護資源。</span><span class="sxs-lookup"><span data-stu-id="315b5-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="315b5-109">在 <xref:System.AppDomain> 內部執行的程式碼會由與 <xref:System.AppDomain> 相關聯的權限繫結，並且僅允許存取指定的資源。</span><span class="sxs-lookup"><span data-stu-id="315b5-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="315b5-110"><xref:System.AppDomain> 也包含 <xref:System.Security.Policy.StrongName> 陣列，用來識別要以完全信任方式載入的組件。</span><span class="sxs-lookup"><span data-stu-id="315b5-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="315b5-111">這可讓 <xref:System.AppDomain> 的建立者啟動新的沙箱定義域，可允許特定協助程式組件變成完全信任。</span><span class="sxs-lookup"><span data-stu-id="315b5-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="315b5-112">另一個以完全信任方式載入組件的選項為將它們放在全域組件快取中；不過，這會在該電腦上建立的應用程式定義域中以完全信任方式載入所有組件。</span><span class="sxs-lookup"><span data-stu-id="315b5-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="315b5-113">強式名稱的清單支援針對每個 <xref:System.AppDomain> 的決策，這會提供更嚴格的判斷。</span><span class="sxs-lookup"><span data-stu-id="315b5-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="315b5-114">您可以使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 方法多載來指定在沙箱中執行的應用程式之權限集。</span><span class="sxs-lookup"><span data-stu-id="315b5-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="315b5-115">這個多載可讓您指定您想要的程式碼存取安全性之確切層級。</span><span class="sxs-lookup"><span data-stu-id="315b5-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="315b5-116">使用這個多載來載入至 <xref:System.AppDomain> 的組件可以只具有指定的授權集，或者可以是完全信任的。</span><span class="sxs-lookup"><span data-stu-id="315b5-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="315b5-117">如果組件位於全域組件快取中或在 `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>) 陣列參數中列出，則會授與組件完全信任。</span><span class="sxs-lookup"><span data-stu-id="315b5-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="315b5-118">只應加入已知為完全信任的組件至 `fullTrustAssemblies` 清單。</span><span class="sxs-lookup"><span data-stu-id="315b5-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="315b5-119">此多載具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="315b5-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="315b5-120"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 方法多載的參數會指定 <xref:System.AppDomain> 的名稱、<xref:System.AppDomain> 的辨識項、會指定沙箱之應用程式基底的 <xref:System.AppDomainSetup> 物件、要使用的授權集，以及完全信任組件的強式名稱。</span><span class="sxs-lookup"><span data-stu-id="315b5-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="315b5-121">基於安全性理由，`info` 參數中指定的應用程式基底不能為裝載應用程式的應用程式基底。</span><span class="sxs-lookup"><span data-stu-id="315b5-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="315b5-122">對於 `grantSet` 參數，您可以指定已明確建立的權限集合或 <xref:System.Security.SecurityManager.GetStandardSandbox%2A> 方法所建立的標準權限集。</span><span class="sxs-lookup"><span data-stu-id="315b5-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="315b5-123">不同於大部分 <xref:System.AppDomain> 的載入，<xref:System.AppDomain> 辨識項 (由 `securityInfo` 參數所提供) 不用來為部分信任的組件判斷授權集。</span><span class="sxs-lookup"><span data-stu-id="315b5-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="315b5-124">相反地，它由 `grantSet` 參數獨立指定。</span><span class="sxs-lookup"><span data-stu-id="315b5-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="315b5-125">不過，辨識項可以用於其他用途，例如判斷隔離儲存區的範圍。</span><span class="sxs-lookup"><span data-stu-id="315b5-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="315b5-126">在沙箱中執行應用程式</span><span class="sxs-lookup"><span data-stu-id="315b5-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="315b5-127">建立要授與給不受信任的應用程式之授權集。</span><span class="sxs-lookup"><span data-stu-id="315b5-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="315b5-128">您可以授與的最小權限是 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 權限。</span><span class="sxs-lookup"><span data-stu-id="315b5-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="315b5-129">您也可授與其他您認為對不受信任的程式碼可能安全的權限；例如 <xref:System.Security.Permissions.IsolatedStorageFilePermission>。</span><span class="sxs-lookup"><span data-stu-id="315b5-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="315b5-130">下列程式碼會建立新的權限集合，其中只有 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 權限。</span><span class="sxs-lookup"><span data-stu-id="315b5-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="315b5-131">或者，您可以使用現有的具名使用權限集合，例如網際網路。</span><span class="sxs-lookup"><span data-stu-id="315b5-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="315b5-132"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> 方法會根據在辨識項中的區域傳回 `Internet` 權限集合或 `LocalIntranet` 權限集合。</span><span class="sxs-lookup"><span data-stu-id="315b5-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="315b5-133">對於某些做為參考傳遞的辨識項物件，<xref:System.Security.SecurityManager.GetStandardSandbox%2A> 也會建構其識別權限。</span><span class="sxs-lookup"><span data-stu-id="315b5-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="315b5-134">簽署包含裝載類別 (在此範例中名為 `Sandboxer`) 的組件，該類別會呼叫不受信任的程式碼。</span><span class="sxs-lookup"><span data-stu-id="315b5-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="315b5-135">加入 <xref:System.Security.Policy.StrongName>，這會用來簽署組件給 <xref:System.AppDomain.CreateDomain%2A> 呼叫的 `fullTrustAssemblies` 參數之 <xref:System.Security.Policy.StrongName> 陣列。</span><span class="sxs-lookup"><span data-stu-id="315b5-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="315b5-136">裝載的類別必須以完全信任方式執行，以啟用部分信任程式碼的執行，或提供服務給部分信任應用程式。</span><span class="sxs-lookup"><span data-stu-id="315b5-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="315b5-137">這就是您讀取組件 <xref:System.Security.Policy.StrongName> 的方式。</span><span class="sxs-lookup"><span data-stu-id="315b5-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="315b5-138">.NET Framework 組件，例如 mscorlib 和 System.dll 就不必加入完全信任清單，因為它們會以完全信任方式從全域組件快取中載入。</span><span class="sxs-lookup"><span data-stu-id="315b5-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="315b5-139">初始化 <xref:System.AppDomain.CreateDomain%2A> 方法的 <xref:System.AppDomainSetup> 參數。</span><span class="sxs-lookup"><span data-stu-id="315b5-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="315b5-140">使用這個參數，您可以控制許多新的 <xref:System.AppDomain> 設定。</span><span class="sxs-lookup"><span data-stu-id="315b5-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="315b5-141"><xref:System.AppDomainSetup.ApplicationBase%2A> 屬性是重要的設定，而且應該不同於裝載應用程式的 <xref:System.AppDomain> 之 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="315b5-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="315b5-142">如果 <xref:System.AppDomainSetup.ApplicationBase%2A> 設定相同，則部分信任應用程式可取得裝載的應用程式，以載入 (以完全信任方式) 它所定義的例外狀況，因而加以利用。</span><span class="sxs-lookup"><span data-stu-id="315b5-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="315b5-143">這是為什麼不建議使用 catch (例外狀況) 的另一個原因。</span><span class="sxs-lookup"><span data-stu-id="315b5-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="315b5-144">將主機的應用程式基底設定為不同於沙箱應用程式的應用程式基底，可減少惡意探索的風險。</span><span class="sxs-lookup"><span data-stu-id="315b5-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="315b5-145">呼叫 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 方法多載來使用我們已指定的參數建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="315b5-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="315b5-146">此方法的簽章是：</span><span class="sxs-lookup"><span data-stu-id="315b5-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="315b5-147">其他資訊：</span><span class="sxs-lookup"><span data-stu-id="315b5-147">Additional information:</span></span>  
  
    - <span data-ttu-id="315b5-148">這是採用 <xref:System.Security.PermissionSet> 做為參數的 <xref:System.AppDomain.CreateDomain%2A> 方法之唯一多載，因此也是讓您在部分信任設定中載入應用程式的唯一多載。</span><span class="sxs-lookup"><span data-stu-id="315b5-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="315b5-149">`evidence` 參數不用來計算權限集合；它由 .NET Framework 的其他功能用來進行識別。</span><span class="sxs-lookup"><span data-stu-id="315b5-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="315b5-150">設定 `info` 參數的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性對於這個多載而言是強制的。</span><span class="sxs-lookup"><span data-stu-id="315b5-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="315b5-151">`fullTrustAssemblies` 參數具有 `params` 關鍵字，這表示不需要建立 <xref:System.Security.Policy.StrongName> 陣列。</span><span class="sxs-lookup"><span data-stu-id="315b5-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="315b5-152">允許將 0、1 或更多的強式名稱當做參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="315b5-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="315b5-153">若要建立應用程式定義域的程式碼是：</span><span class="sxs-lookup"><span data-stu-id="315b5-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="315b5-154">將程式碼載入您所建立的沙箱 <xref:System.AppDomain> 中。</span><span class="sxs-lookup"><span data-stu-id="315b5-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="315b5-155">有兩種方法可以達到這個目的：</span><span class="sxs-lookup"><span data-stu-id="315b5-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="315b5-156">呼叫組件的 <xref:System.AppDomain.ExecuteAssembly%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="315b5-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="315b5-157">使用 <xref:System.Activator.CreateInstanceFrom%2A> 方法在新的 <xref:System.AppDomain> 建立衍生自 <xref:System.MarshalByRefObject> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="315b5-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="315b5-158">第二種方法更合適，因為它讓您更輕鬆地將參數傳遞給新的 <xref:System.AppDomain> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="315b5-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="315b5-159"><xref:System.Activator.CreateInstanceFrom%2A> 方法提供兩個重要功能：</span><span class="sxs-lookup"><span data-stu-id="315b5-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="315b5-160">您可使用會指向不包含組件位置的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="315b5-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="315b5-161">您可以在 <xref:System.Security.CodeAccessPermission.Assert%2A> 之下建立完全信任 (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>)，這可讓您建立關鍵類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="315b5-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="315b5-162">(每當您的組件不具有透明度標記，且以完全信任方式載入時就會發生)。因此您應特別小心，只能建立您信任此函式的程式碼，我們建議您在新的應用程式定義域中只建立完全信任類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="315b5-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="315b5-163">請注意若要在新的定義域中建立類別的執行個體，此類別必須擴充 <xref:System.MarshalByRefObject> 類別</span><span class="sxs-lookup"><span data-stu-id="315b5-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="315b5-164">解除包裝新定義域之執行個體至此定義域的參考。</span><span class="sxs-lookup"><span data-stu-id="315b5-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="315b5-165">這個參考用來執行不受信任的程式碼。</span><span class="sxs-lookup"><span data-stu-id="315b5-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="315b5-166">請在您剛建立的 `Sandboxer` 類別之執行個體中呼叫 `ExecuteUntrustedCode` 方法。</span><span class="sxs-lookup"><span data-stu-id="315b5-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="315b5-167">這個呼叫會在沙箱應用程式定義域中執行，具有受限制的使用權限。</span><span class="sxs-lookup"><span data-stu-id="315b5-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="315b5-168"><xref:System.Reflection> 用來在部分信任組件中取得方法的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="315b5-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="315b5-169">控制代碼可用來以安全的方式搭配最小權限執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="315b5-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="315b5-170">在先前的程式碼中，請先注意完全信任權限的 <xref:System.Security.PermissionSet.Assert%2A>，然後才列印 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="315b5-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="315b5-171">完全信任的判斷提示用來從 <xref:System.Security.SecurityException> 取得擴充的資訊。</span><span class="sxs-lookup"><span data-stu-id="315b5-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="315b5-172">在沒有 <xref:System.Security.PermissionSet.Assert%2A> 的情況下，<xref:System.Security.SecurityException> 的 <xref:System.Security.SecurityException.ToString%2A> 方法會在堆疊上探索部分信任程式碼，並且限制傳回的資訊。</span><span class="sxs-lookup"><span data-stu-id="315b5-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="315b5-173">如果部分信任程式碼可能讀取該資訊，則這可能會造成安全性問題，但不授與 <xref:System.Security.Permissions.UIPermission> 可降低風險。</span><span class="sxs-lookup"><span data-stu-id="315b5-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="315b5-174">應該謹慎使用完全信任的判斷提示，而且僅當您確定不允許部分信任程式碼提升為完全信任時才能使用。</span><span class="sxs-lookup"><span data-stu-id="315b5-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="315b5-175">在相同的函式中，以及為了完全信任而呼叫判斷提示之後，通常請不要呼叫您不信任的程式碼。</span><span class="sxs-lookup"><span data-stu-id="315b5-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="315b5-176">當您使用完畢後，一律將判斷提示還原會是最佳的做法。</span><span class="sxs-lookup"><span data-stu-id="315b5-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="315b5-177">範例</span><span class="sxs-lookup"><span data-stu-id="315b5-177">Example</span></span>  
 <span data-ttu-id="315b5-178">下列範例會實作上一節中的程序。</span><span class="sxs-lookup"><span data-stu-id="315b5-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="315b5-179">在此範例中，Visual Studio 方案裡名為 `Sandboxer` 的專案還包含一個名為 `UntrustedCode` 的專案，這會實作 `UntrustedClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="315b5-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="315b5-180">此案例假定您已下載包含方法的程式庫組件，該方法預期會傳回 `true` 或 `false` 來指出您提供的數字是否為費式數列。</span><span class="sxs-lookup"><span data-stu-id="315b5-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="315b5-181">相反地，該方法會嘗試從您的電腦讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="315b5-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="315b5-182">下列範例顯示未受信任的程式碼。</span><span class="sxs-lookup"><span data-stu-id="315b5-182">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="315b5-183">下列範例顯示執行不受信任程式碼的 `Sandboxer` 應用程式之程式碼。</span><span class="sxs-lookup"><span data-stu-id="315b5-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="315b5-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="315b5-184">See also</span></span>

- [<span data-ttu-id="315b5-185">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="315b5-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
