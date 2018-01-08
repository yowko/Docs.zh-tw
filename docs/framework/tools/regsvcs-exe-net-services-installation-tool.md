---
title: "Regsvcs.exe (.NET 服務安裝工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd7f50d591232feda0259ecefdb5b9e39514ccb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="94685-102">Regsvcs.exe (.NET 服務安裝工具)</span><span class="sxs-lookup"><span data-stu-id="94685-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="94685-103">.NET 服務安裝工具會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="94685-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
-   <span data-ttu-id="94685-104">載入和註冊組件。</span><span class="sxs-lookup"><span data-stu-id="94685-104">Loads and registers an assembly.</span></span>  
  
-   <span data-ttu-id="94685-105">產生、註冊和安裝類型程式庫到指定的 COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="94685-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
-   <span data-ttu-id="94685-106">設定您以程式設計方式加入至類別的服務。</span><span class="sxs-lookup"><span data-stu-id="94685-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="94685-107">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="94685-107">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="94685-108">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="94685-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="94685-109">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="94685-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94685-110">語法</span><span class="sxs-lookup"><span data-stu-id="94685-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a><span data-ttu-id="94685-111">參數</span><span class="sxs-lookup"><span data-stu-id="94685-111">Parameters</span></span>  
  
|<span data-ttu-id="94685-112">引數</span><span class="sxs-lookup"><span data-stu-id="94685-112">Argument</span></span>|<span data-ttu-id="94685-113">描述</span><span class="sxs-lookup"><span data-stu-id="94685-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="94685-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="94685-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="94685-115">來源組件檔。</span><span class="sxs-lookup"><span data-stu-id="94685-115">The source assembly file.</span></span> <span data-ttu-id="94685-116">這個組件必須以強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="94685-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="94685-117">如需詳細資訊，請參閱[以強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="94685-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="94685-118">選項</span><span class="sxs-lookup"><span data-stu-id="94685-118">Option</span></span>|<span data-ttu-id="94685-119">描述</span><span class="sxs-lookup"><span data-stu-id="94685-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="94685-120">**/appdir:<路徑>** </span><span class="sxs-lookup"><span data-stu-id="94685-120">**/appdir:** *path*</span></span>|<span data-ttu-id="94685-121">指定應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="94685-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="94685-122">**/appname:<應用程式名稱>** </span><span class="sxs-lookup"><span data-stu-id="94685-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="94685-123">指定要尋找或建立之 COM+ 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="94685-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="94685-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="94685-124">**/c**</span></span>|<span data-ttu-id="94685-125">建立目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="94685-125">Creates the target application.</span></span>|  
|<span data-ttu-id="94685-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="94685-126">**/componly**</span></span>|<span data-ttu-id="94685-127">只設定元件，忽略方法和介面。</span><span class="sxs-lookup"><span data-stu-id="94685-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="94685-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="94685-128">**/exapp**</span></span>|<span data-ttu-id="94685-129">指定需要現有應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="94685-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="94685-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="94685-130">**/extlb**</span></span>|<span data-ttu-id="94685-131">使用現有的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="94685-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="94685-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="94685-132">**/fc**</span></span>|<span data-ttu-id="94685-133">尋找或建立目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="94685-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="94685-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="94685-134">**/help**</span></span>|<span data-ttu-id="94685-135">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="94685-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="94685-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="94685-136">**/noreconfig**</span></span>|<span data-ttu-id="94685-137">不要重新設定現有的目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="94685-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="94685-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="94685-138">**/nologo**</span></span>|<span data-ttu-id="94685-139">隱藏 Microsoft 程式啟始資訊顯示。</span><span class="sxs-lookup"><span data-stu-id="94685-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="94685-140">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="94685-140">**/parname:** *name*</span></span>|<span data-ttu-id="94685-141">指定要尋找或建立之 COM+ 應用程式的名稱或 ID。</span><span class="sxs-lookup"><span data-stu-id="94685-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="94685-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="94685-142">**/reconfig**</span></span>|<span data-ttu-id="94685-143">重新設定現有的目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="94685-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="94685-144">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="94685-144">This is the default.</span></span>|  
|<span data-ttu-id="94685-145">**/tlb:<型別程式庫檔案>** </span><span class="sxs-lookup"><span data-stu-id="94685-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="94685-146">指定要安裝的類型程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="94685-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="94685-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="94685-147">**/u**</span></span>|<span data-ttu-id="94685-148">解除安裝目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="94685-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="94685-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="94685-149">**/quiet**</span></span>|<span data-ttu-id="94685-150">指定安靜模式，隱藏標誌或成功訊息顯示。</span><span class="sxs-lookup"><span data-stu-id="94685-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="94685-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="94685-151">**/?**</span></span>|<span data-ttu-id="94685-152">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="94685-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94685-153">備註</span><span class="sxs-lookup"><span data-stu-id="94685-153">Remarks</span></span>  
 <span data-ttu-id="94685-154">Regsvcs.exe 需要由 *assemblyFile.dll* 所指定的來源組件檔。</span><span class="sxs-lookup"><span data-stu-id="94685-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="94685-155">這個組件必須使用強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="94685-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="94685-156">如需強式名稱簽署的詳細資訊，請參閱[以強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="94685-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="94685-157">目標應用程式和類型程式庫檔案的名稱是選擇項。</span><span class="sxs-lookup"><span data-stu-id="94685-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="94685-158">如果 *applicationName* 引數已經不存在，則可以從來源組件檔中產生，並且將會由 Regsvcs.exe 建立。</span><span class="sxs-lookup"><span data-stu-id="94685-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="94685-159">*typelibraryfile* 引數可以指定型別程式庫名稱。</span><span class="sxs-lookup"><span data-stu-id="94685-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="94685-160">如果您沒有指定類型程式庫名稱，Regsvcs.exe 會使用組件名稱做為預設值。</span><span class="sxs-lookup"><span data-stu-id="94685-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="94685-161">當 Regsvcs.exe 註冊元件的方法時，它會受制於這些方法上的[要求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)和[連結要求](../../../docs/framework/misc/link-demands.md)。</span><span class="sxs-lookup"><span data-stu-id="94685-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="94685-162">因為這個工具是在完全信任的環境中執行，所以大部分的使用權限需求都會成功。</span><span class="sxs-lookup"><span data-stu-id="94685-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="94685-163">不過，Regsvcs.exe 無法註冊方法受到 <xref:System.Security.Permissions.StrongNameIdentityPermission> 或 <xref:System.Security.Permissions.PublisherIdentityPermission> 的需求或連結要求保護的元件。</span><span class="sxs-lookup"><span data-stu-id="94685-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="94685-164">您必須擁有本機電腦上的系統管理員權限，才能使用 Regsvcs.exe。</span><span class="sxs-lookup"><span data-stu-id="94685-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="94685-165">在執行任何這些動作時，如果 Regsvcs.exe 失敗，會顯示對應的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="94685-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="94685-166">範例</span><span class="sxs-lookup"><span data-stu-id="94685-166">Examples</span></span>  
 <span data-ttu-id="94685-167">下列命令會將 `myTest.dll` 中包含的所有公用類別加入 `myTargetApp` (現有的 COM+ 應用程式)，並產生 `myTest.tlb` 類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="94685-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="94685-168">下列命令會將 `myTest.dll` 中包含的所有公用類別加入 `myTargetApp` (現有的 COM+ 應用程式)，並產生 `newTest.tlb` 類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="94685-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="94685-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="94685-169">See Also</span></span>  
 [<span data-ttu-id="94685-170">工具</span><span class="sxs-lookup"><span data-stu-id="94685-170">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="94685-171">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="94685-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="94685-172">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="94685-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
