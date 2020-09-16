---
title: Regsvcs.exe (.NET 服務安裝工具)
description: 使用 Regsvcs.exe （.NET 服務安裝工具）。 載入並註冊元件、設定您以程式設計方式新增至類別的服務等等。
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 474018b8bc39e4d5c36bd4bc6481072b218d6270
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558390"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="87ff9-104">Regsvcs.exe (.NET 服務安裝工具)</span><span class="sxs-lookup"><span data-stu-id="87ff9-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="87ff9-105">.NET 服務安裝工具會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="87ff9-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="87ff9-106">載入和註冊組件。</span><span class="sxs-lookup"><span data-stu-id="87ff9-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="87ff9-107">產生、註冊和安裝類型程式庫到指定的 COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="87ff9-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="87ff9-108">設定您以程式設計方式加入至類別的服務。</span><span class="sxs-lookup"><span data-stu-id="87ff9-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="87ff9-109">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="87ff9-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="87ff9-110">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="87ff9-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="87ff9-111">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="87ff9-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ff9-112">語法</span><span class="sxs-lookup"><span data-stu-id="87ff9-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="87ff9-113">參數</span><span class="sxs-lookup"><span data-stu-id="87ff9-113">Parameters</span></span>  
  
|<span data-ttu-id="87ff9-114">引數</span><span class="sxs-lookup"><span data-stu-id="87ff9-114">Argument</span></span>|<span data-ttu-id="87ff9-115">描述</span><span class="sxs-lookup"><span data-stu-id="87ff9-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="87ff9-116">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="87ff9-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="87ff9-117">來源組件檔。</span><span class="sxs-lookup"><span data-stu-id="87ff9-117">The source assembly file.</span></span> <span data-ttu-id="87ff9-118">這個組件必須以強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="87ff9-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="87ff9-119">如需詳細資訊，請參閱[以強式名稱簽署組件](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="87ff9-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="87ff9-120">選項</span><span class="sxs-lookup"><span data-stu-id="87ff9-120">Option</span></span>|<span data-ttu-id="87ff9-121">描述</span><span class="sxs-lookup"><span data-stu-id="87ff9-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="87ff9-122">**/appdir:<路徑>** \*\*</span><span class="sxs-lookup"><span data-stu-id="87ff9-122">**/appdir:** *path*</span></span>|<span data-ttu-id="87ff9-123">指定應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="87ff9-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="87ff9-124">**/appname:<應用程式名稱>** \*\*</span><span class="sxs-lookup"><span data-stu-id="87ff9-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="87ff9-125">指定要尋找或建立之 COM+ 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="87ff9-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="87ff9-126">**/c**</span><span class="sxs-lookup"><span data-stu-id="87ff9-126">**/c**</span></span>|<span data-ttu-id="87ff9-127">建立目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="87ff9-127">Creates the target application.</span></span>|  
|<span data-ttu-id="87ff9-128">**/componly**</span><span class="sxs-lookup"><span data-stu-id="87ff9-128">**/componly**</span></span>|<span data-ttu-id="87ff9-129">只設定元件，忽略方法和介面。</span><span class="sxs-lookup"><span data-stu-id="87ff9-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="87ff9-130">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="87ff9-130">**/exapp**</span></span>|<span data-ttu-id="87ff9-131">指定需要現有應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="87ff9-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="87ff9-132">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="87ff9-132">**/extlb**</span></span>|<span data-ttu-id="87ff9-133">使用現有的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="87ff9-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="87ff9-134">**/fc**</span><span class="sxs-lookup"><span data-stu-id="87ff9-134">**/fc**</span></span>|<span data-ttu-id="87ff9-135">尋找或建立目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="87ff9-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="87ff9-136">**/help**</span><span class="sxs-lookup"><span data-stu-id="87ff9-136">**/help**</span></span>|<span data-ttu-id="87ff9-137">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="87ff9-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="87ff9-138">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="87ff9-138">**/noreconfig**</span></span>|<span data-ttu-id="87ff9-139">不要重新設定現有的目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="87ff9-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="87ff9-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="87ff9-140">**/nologo**</span></span>|<span data-ttu-id="87ff9-141">隱藏 Microsoft 程式啟始資訊顯示。</span><span class="sxs-lookup"><span data-stu-id="87ff9-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="87ff9-142">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="87ff9-142">**/parname:** *name*</span></span>|<span data-ttu-id="87ff9-143">指定要尋找或建立之 COM+ 應用程式的名稱或 ID。</span><span class="sxs-lookup"><span data-stu-id="87ff9-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="87ff9-144">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="87ff9-144">**/reconfig**</span></span>|<span data-ttu-id="87ff9-145">重新設定現有的目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="87ff9-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="87ff9-146">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="87ff9-146">This is the default.</span></span>|  
|<span data-ttu-id="87ff9-147">**/tlb:<型別程式庫檔案>** \*\*</span><span class="sxs-lookup"><span data-stu-id="87ff9-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="87ff9-148">指定要安裝的類型程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="87ff9-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="87ff9-149">**u**</span><span class="sxs-lookup"><span data-stu-id="87ff9-149">**/u**</span></span>|<span data-ttu-id="87ff9-150">解除安裝目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="87ff9-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="87ff9-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="87ff9-151">**/quiet**</span></span>|<span data-ttu-id="87ff9-152">指定安靜模式，隱藏標誌或成功訊息顯示。</span><span class="sxs-lookup"><span data-stu-id="87ff9-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="87ff9-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="87ff9-153">**/?**</span></span>|<span data-ttu-id="87ff9-154">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="87ff9-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87ff9-155">備註</span><span class="sxs-lookup"><span data-stu-id="87ff9-155">Remarks</span></span>  
 <span data-ttu-id="87ff9-156">Regsvcs.exe 需要由 *assemblyFile.dll* 所指定的來源組件檔。</span><span class="sxs-lookup"><span data-stu-id="87ff9-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="87ff9-157">這個組件必須使用強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="87ff9-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="87ff9-158">如需強式名稱簽署的詳細資訊，請參閱[以強式名稱簽署組件](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="87ff9-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="87ff9-159">目標應用程式和類型程式庫檔案的名稱是選擇項。</span><span class="sxs-lookup"><span data-stu-id="87ff9-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="87ff9-160">如果 *applicationName* 引數已經不存在，則可以從來源組件檔中產生，並且將會由 Regsvcs.exe 建立。</span><span class="sxs-lookup"><span data-stu-id="87ff9-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="87ff9-161">*typelibraryfile* 引數可以指定型別程式庫名稱。</span><span class="sxs-lookup"><span data-stu-id="87ff9-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="87ff9-162">如果您沒有指定類型程式庫名稱，Regsvcs.exe 會使用組件名稱做為預設值。</span><span class="sxs-lookup"><span data-stu-id="87ff9-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="87ff9-163">當 Regsvcs.exe 註冊元件的方法時，它會受制於這些方法上的[要求](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100))和[連結要求](../misc/link-demands.md)。</span><span class="sxs-lookup"><span data-stu-id="87ff9-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="87ff9-164">因為這個工具是在完全信任的環境中執行，所以大部分的使用權限需求都會成功。</span><span class="sxs-lookup"><span data-stu-id="87ff9-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="87ff9-165">不過，Regsvcs.exe 無法註冊方法受到 <xref:System.Security.Permissions.StrongNameIdentityPermission> 或 <xref:System.Security.Permissions.PublisherIdentityPermission> 的需求或連結要求保護的元件。</span><span class="sxs-lookup"><span data-stu-id="87ff9-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="87ff9-166">您必須擁有本機電腦上的系統管理員權限，才能使用 Regsvcs.exe。</span><span class="sxs-lookup"><span data-stu-id="87ff9-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="87ff9-167">在執行任何這些動作時，如果 Regsvcs.exe 失敗，會顯示對應的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="87ff9-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="87ff9-168">範例</span><span class="sxs-lookup"><span data-stu-id="87ff9-168">Examples</span></span>  
 <span data-ttu-id="87ff9-169">下列命令會將 `myTest.dll` 中包含的所有公用類別加入 `myTargetApp` (現有的 COM+ 應用程式)，並產生 `myTest.tlb` 類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="87ff9-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="87ff9-170">下列命令會將 `myTest.dll` 中包含的所有公用類別加入 `myTargetApp` (現有的 COM+ 應用程式)，並產生 `newTest.tlb` 類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="87ff9-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="87ff9-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87ff9-171">See also</span></span>

- [<span data-ttu-id="87ff9-172">工具</span><span class="sxs-lookup"><span data-stu-id="87ff9-172">Tools</span></span>](index.md)
- [<span data-ttu-id="87ff9-173">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="87ff9-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="87ff9-174">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="87ff9-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
