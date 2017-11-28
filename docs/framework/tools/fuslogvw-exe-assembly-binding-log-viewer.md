---
title: "Fuslogvw.exe (組件繫結記錄檔檢視器)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ad02ade9c9e60e53fa8fb91d9a38d6ec12bc2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="69c70-102">Fuslogvw.exe (組件繫結記錄檔檢視器)</span><span class="sxs-lookup"><span data-stu-id="69c70-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>
<span data-ttu-id="69c70-103">組件繫結記錄檔檢視器會顯示組件繫結的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="69c70-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="69c70-104">這項資訊有助於診斷 .NET Framework 為何無法在執行階段找到組件。</span><span class="sxs-lookup"><span data-stu-id="69c70-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="69c70-105">這類失敗通常是因為組件部署至不正確的位置、原生映像已失效，或版本號碼或文化特定不符所致。</span><span class="sxs-lookup"><span data-stu-id="69c70-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="69c70-106">通用語言執行平台找不到組件，通常在應用程式中會顯示為 <xref:System.TypeLoadException>。</span><span class="sxs-lookup"><span data-stu-id="69c70-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69c70-107">您必須以系統管理員權限執行 fuslogvw.exe。</span><span class="sxs-lookup"><span data-stu-id="69c70-107">You must run fuslogvw.exe with administrator privileges.</span></span>  
  
 <span data-ttu-id="69c70-108">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="69c70-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="69c70-109">若要執行這項工具，請使用具有系統管理員認證的開發人員命令提示字元 (或 Windows 7 中的 Visual Studio 命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="69c70-109">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="69c70-110">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="69c70-110">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="69c70-111">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="69c70-111">At the command prompt, type the following:</span></span>  
  
```  
fuslogvw  
```  
  
 <span data-ttu-id="69c70-112">檢視器會針對每一個失敗的組件繫結顯示一個項目。</span><span class="sxs-lookup"><span data-stu-id="69c70-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="69c70-113">針對每一項失敗，檢視器會描述啟始該繫結的應用程式、所要繫結的組件 (包括名稱、版本、文化特性和公開金鑰)，以及失敗的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="69c70-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>  
  
### <a name="to-change-the-log-location-view"></a><span data-ttu-id="69c70-114">若要變更記錄檔位置檢視</span><span class="sxs-lookup"><span data-stu-id="69c70-114">To change the log location view</span></span>  
  
1.  <span data-ttu-id="69c70-115">選取 [預設值] 選項按鈕，可檢視所有應用程式類型的繫結失敗。</span><span class="sxs-lookup"><span data-stu-id="69c70-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="69c70-116">根據預設，記錄項目會存放在 wininet 快取中磁碟上的每個使用者目錄中。</span><span class="sxs-lookup"><span data-stu-id="69c70-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>  
  
2.  <span data-ttu-id="69c70-117">選取 [自訂] 選項按鈕，可檢視您指定之自訂目錄中的繫結失敗。</span><span class="sxs-lookup"><span data-stu-id="69c70-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="69c70-118">您必須透過將 [記錄檔設定] 對話方塊中的自訂記錄檔路徑設為有效的目錄名稱，指定要讓執行階段存放記錄檔的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="69c70-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="69c70-119">這個目錄應該是乾淨的，只包含執行階段產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="69c70-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="69c70-120">如果它包含會產生失敗記錄的可執行檔，則失敗將不會記錄下來，因為工具會嘗試使用與該可執行檔相同的名稱建立目錄。</span><span class="sxs-lookup"><span data-stu-id="69c70-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="69c70-121">此外，嘗試從記錄檔位置執行可執行檔將會失敗。</span><span class="sxs-lookup"><span data-stu-id="69c70-121">In addition, an attempt to run an executable from the log location will fail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69c70-122">預設繫結位置要比自訂繫結位置更合適。</span><span class="sxs-lookup"><span data-stu-id="69c70-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="69c70-123">執行階段會將預設繫結位置存放到 wininet 快取中，因此會自動將它清除。如果您指定自訂繫結位置，則必須負責將它清除。</span><span class="sxs-lookup"><span data-stu-id="69c70-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>  
  
### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="69c70-124">若要檢視特定失敗的詳細資料</span><span class="sxs-lookup"><span data-stu-id="69c70-124">To view details about a specific failure</span></span>  
  
1.  <span data-ttu-id="69c70-125">在檢視器中選取所需項目的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="69c70-125">Select the application name of the desired entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="69c70-126">按一下 [檢視記錄檔] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-126">Click the **View Log** button.</span></span> <span data-ttu-id="69c70-127">或者，您也可以按兩下選取的項目。</span><span class="sxs-lookup"><span data-stu-id="69c70-127">Alternately, you can double-click the selected entry.</span></span>  
  
     <span data-ttu-id="69c70-128">工具便會顯示有關所選取繫結失敗的下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="69c70-128">The tool displays the following details about the selected bind failure:</span></span>  
  
    -   <span data-ttu-id="69c70-129">繫結失敗的特定原因，例如「找不到檔案」或「版本不符」。</span><span class="sxs-lookup"><span data-stu-id="69c70-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>  
  
    -   <span data-ttu-id="69c70-130">啟始繫結之應用程式的相關資訊，包括其名稱、應用程式的根目錄 (AppBase) 以及私用搜尋路徑的描述 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="69c70-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>  
  
    -   <span data-ttu-id="69c70-131">工具所搜尋之組件的識別。</span><span class="sxs-lookup"><span data-stu-id="69c70-131">The identity of the assembly the tool is looking for.</span></span>  
  
    -   <span data-ttu-id="69c70-132">已套用之任何應用程式、發行者或系統管理員版本原則的描述。</span><span class="sxs-lookup"><span data-stu-id="69c70-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>  
  
    -   <span data-ttu-id="69c70-133">在[全域組件快取](../../../docs/framework/app-domains/gac.md)中是否找到組件。</span><span class="sxs-lookup"><span data-stu-id="69c70-133">Whether the assembly was found in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span>  
  
    -   <span data-ttu-id="69c70-134">所有探查 URL 的清單。</span><span class="sxs-lookup"><span data-stu-id="69c70-134">A list of all probing URLs.</span></span>  
  
 <span data-ttu-id="69c70-135">以下範例記錄項目將顯示失敗之組件繫結的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="69c70-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>  
  
```  
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll  
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe  
--- A detailed error log follows.   
  
=== Pre-bind state information ===  
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
 (Fully-specified)  
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\  
LOG: Initial PrivatePath = NULL  
LOG: Dynamic Base = NULL  
LOG: Cache Base = NULL  
LOG: AppName = NULL  
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
===  
  
LOG: Processing DEVPATH.  
LOG: DEVPATH is not set. Falling through to regular bind.  
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).  
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.  
LOG: All probing URLs attempted and failed.  
```  
  
### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="69c70-136">若要從記錄檔刪除單一項目</span><span class="sxs-lookup"><span data-stu-id="69c70-136">To delete a single entry from the log</span></span>  
  
1.  <span data-ttu-id="69c70-137">在檢視器中選取項目。</span><span class="sxs-lookup"><span data-stu-id="69c70-137">Select an entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="69c70-138">按一下 [刪除項目] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-138">Click the **Delete Entry** button.</span></span>  
  
### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="69c70-139">若要從記錄檔刪除所有項目</span><span class="sxs-lookup"><span data-stu-id="69c70-139">To delete all entries from the log</span></span>  
  
-   <span data-ttu-id="69c70-140">按一下 [全部刪除] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-140">Click the **Delete All** button.</span></span>  
  
### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="69c70-141">若要重新整理使用者介面</span><span class="sxs-lookup"><span data-stu-id="69c70-141">To refresh the user interface</span></span>  
  
-   <span data-ttu-id="69c70-142">按一下 [重新整理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-142">Click the **Refresh** button.</span></span> <span data-ttu-id="69c70-143">檢視器在執行時不會自動偵測新的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="69c70-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="69c70-144">您必須使用 [重新整理] 按鈕才能顯示新項目。</span><span class="sxs-lookup"><span data-stu-id="69c70-144">You must use the **Refresh** button to display them.</span></span>  
  
### <a name="to-change-the-log-settings"></a><span data-ttu-id="69c70-145">若要變更記錄檔設定</span><span class="sxs-lookup"><span data-stu-id="69c70-145">To change the log settings</span></span>  
  
-   <span data-ttu-id="69c70-146">按一下 [設定] 按鈕，開啟 [記錄檔設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="69c70-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>  
  
### <a name="to-view-the-about-dialog"></a><span data-ttu-id="69c70-147">若要檢視關於對話方塊</span><span class="sxs-lookup"><span data-stu-id="69c70-147">To view the About dialog</span></span>  
  
-   <span data-ttu-id="69c70-148">按一下 [關於] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-148">Click the **About** button.</span></span>  
  
## <a name="binding-logs-for-native-images"></a><span data-ttu-id="69c70-149">原生映像的繫結記錄檔</span><span class="sxs-lookup"><span data-stu-id="69c70-149">Binding Logs for Native Images</span></span>  
 <span data-ttu-id="69c70-150">根據預設，Fuslogvw.exe 會記錄正常的組件繫結要求。</span><span class="sxs-lookup"><span data-stu-id="69c70-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="69c70-151">或者，您可以記錄使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 所建立之原生映像的組件繫結。</span><span class="sxs-lookup"><span data-stu-id="69c70-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="69c70-152">若要記錄原生映像的組件繫結</span><span class="sxs-lookup"><span data-stu-id="69c70-152">To log assembly binds for native images</span></span>  
  
-   <span data-ttu-id="69c70-153">在 [記錄檔分類] 群組中，選取 [原生映像] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>  
  
 <span data-ttu-id="69c70-154">下列記錄將顯示建立應用程式的原生影像時，不存在的相依性所造成的失敗。</span><span class="sxs-lookup"><span data-stu-id="69c70-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="69c70-155">如果執行階段的相依性與 Ngen.exe 執行時的相依性不同，則不允許繫結至原生映像。</span><span class="sxs-lookup"><span data-stu-id="69c70-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\App.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\App.exe.  
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.  
WRN: No matching native image found.  
LOG: Bind to native image assembly did not succeed. Use IL image.  
```  
  
 <span data-ttu-id="69c70-156">下列記錄檔顯示的原生映像繫結失敗，是由於應用程式執行時電腦上的安全性設定，與原生映像建立時的安全性設定不同所致。</span><span class="sxs-lookup"><span data-stu-id="69c70-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80004005. Unspecified error  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\Application101622.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\Application101622.exe.  
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Dependency evaluation succeeded.  
LOG: Validation of dependencies succeeded.  
LOG: Start loading all the dependencies into load context.  
LOG: Loading of dependencies succeeded.  
LOG: Bind to native image succeeded.  
Native image has correct version information.  
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.  
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.  
Discarding native image.  
```  
  
## <a name="the-log-settings-dialog"></a><span data-ttu-id="69c70-157">[記錄檔設定] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="69c70-157">The Log Settings Dialog</span></span>  
 <span data-ttu-id="69c70-158">您可以使用 [記錄檔設定] 對話方塊執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="69c70-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>  
  
#### <a name="to-disable-logging"></a><span data-ttu-id="69c70-159">若要停用記錄</span><span class="sxs-lookup"><span data-stu-id="69c70-159">To disable logging</span></span>  
  
-   <span data-ttu-id="69c70-160">選取 [停用記錄] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="69c70-161">請注意，這個選項預設為選取狀態。</span><span class="sxs-lookup"><span data-stu-id="69c70-161">Note that this option is selected by default.</span></span>  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="69c70-162">若要記錄例外狀況中的組件繫結</span><span class="sxs-lookup"><span data-stu-id="69c70-162">To log assembly binds in exceptions</span></span>  
  
-   <span data-ttu-id="69c70-163">選取 [在例外狀況文字中記錄] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="69c70-164">例外狀況文字中只會記錄最簡要的融合記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="69c70-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="69c70-165">若要檢視完整資訊，請使用其中一項其他設定。</span><span class="sxs-lookup"><span data-stu-id="69c70-165">To view full information, use one of the other settings.</span></span>  
  
     <span data-ttu-id="69c70-166">請參閱有關以定義域中性方式載入之組件的＜重要事項＞。</span><span class="sxs-lookup"><span data-stu-id="69c70-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="69c70-167">若要記錄組件繫結失敗</span><span class="sxs-lookup"><span data-stu-id="69c70-167">To log assembly bind failures</span></span>  
  
-   <span data-ttu-id="69c70-168">選取 [在磁碟中記錄失敗的繫結] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-168">Select the **Log bind failures to disk** option button.</span></span>  
  
     <span data-ttu-id="69c70-169">請參閱有關以定義域中性方式載入之組件的＜重要事項＞。</span><span class="sxs-lookup"><span data-stu-id="69c70-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="69c70-170">若要記錄所有組件繫結</span><span class="sxs-lookup"><span data-stu-id="69c70-170">To log all assembly binds</span></span>  
  
-   <span data-ttu-id="69c70-171">選取 [在磁碟中記錄所有繫結] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-171">Select the **Log all binds to disk** option button.</span></span>  
  
     <span data-ttu-id="69c70-172">請參閱有關以定義域中性方式載入之組件的＜重要事項＞。</span><span class="sxs-lookup"><span data-stu-id="69c70-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69c70-173">以定義域中性方式載入組件時 (例如，將 <xref:System.AppDomainSetup.LoaderOptimization%2A> 屬性設定為 <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> 或 <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>)，開啟記錄功能在某些情況下可能會造成記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="69c70-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="69c70-174">如果在將定義域中性模組載入至應用程式定義域時加入一筆記錄項目，稍後卸載應用程式定義域時，便可能發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="69c70-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="69c70-175">在處理序結束之前，可能都不會發行這個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="69c70-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="69c70-176">有些偵錯工具會自動開啟記錄功能。</span><span class="sxs-lookup"><span data-stu-id="69c70-176">Some debuggers automatically turn on logging.</span></span>  
  
#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="69c70-177">若要啟用自訂記錄檔路徑</span><span class="sxs-lookup"><span data-stu-id="69c70-177">To enable a custom log path</span></span>  
  
1.  <span data-ttu-id="69c70-178">選取 [啟用自訂的記錄檔路徑] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="69c70-178">Select the **Enable custom log path** option button.</span></span>  
  
2.  <span data-ttu-id="69c70-179">在 [自訂的記錄檔路徑] 文字方塊中輸入路徑。</span><span class="sxs-lookup"><span data-stu-id="69c70-179">Enter the path into the **Custom log path** text box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69c70-180">[組件繫結記錄檔檢視器 (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) 使用 Internet Explorer (IE) 快取來儲存其繫結記錄檔。</span><span class="sxs-lookup"><span data-stu-id="69c70-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="69c70-181">由於 IE 快取偶爾會損毀，因此[組件繫結記錄檔檢視器 (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) 有時可能會停止在檢視視窗內顯示新的繫結記錄檔。</span><span class="sxs-lookup"><span data-stu-id="69c70-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="69c70-182">這種損毀導致 .NET 繫結基礎結構 (融合) 無法寫入繫結記錄檔或從繫結記錄檔讀取 </span><span class="sxs-lookup"><span data-stu-id="69c70-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="69c70-183">(如果您使用自訂的記錄檔路徑，就不會發生這個問題)。若要修復損毀並讓融合再次顯示繫結記錄檔，請從 IE 的 [網際網路選項] 對話方塊中刪除網際網路暫存檔 (Temporary Internet Files)，以便清除 IE 快取。</span><span class="sxs-lookup"><span data-stu-id="69c70-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>  
>   
>  <span data-ttu-id="69c70-184">如果 Unmanaged 應用程式藉由實作 `IHostAssemblyManager` 和 `IHostAssemblyStore` 介面裝載 Common Language Runtime，則無法將記錄項目儲存在 wininet 快取中。</span><span class="sxs-lookup"><span data-stu-id="69c70-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="69c70-185">若要檢視實作這些介面之自訂主機的記錄項目，則必須指定替代的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="69c70-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="69c70-186">若要啟用在 Windows 應用程式容器中執行的應用程式記錄功能</span><span class="sxs-lookup"><span data-stu-id="69c70-186">To enable logging for apps running in the Windows app container</span></span>  
  
1.  <span data-ttu-id="69c70-187">啟用自訂的記錄檔路徑，如上述程序所述。</span><span class="sxs-lookup"><span data-stu-id="69c70-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="69c70-188">根據預設，在 Windows 應用程式容器中執行的應用程式對硬碟的存取權會受到限制。</span><span class="sxs-lookup"><span data-stu-id="69c70-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="69c70-189">您指定的目錄將可以對應用程式容器中的所有應用程式進行讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="69c70-189">The directory you specify will have read/write access for all apps in the app container.</span></span>  
  
2.  <span data-ttu-id="69c70-190">選取 [啟用擬真記錄] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="69c70-190">Select the **Enable immersive logging** check box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69c70-191">只有在 Windows 8 (含) 以後版本中才會啟用這個方塊。</span><span class="sxs-lookup"><span data-stu-id="69c70-191">This box is enabled only on Windows 8 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c70-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69c70-192">See Also</span></span>  
 <xref:System.TypeLoadException>  
 [<span data-ttu-id="69c70-193">工具</span><span class="sxs-lookup"><span data-stu-id="69c70-193">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="69c70-194">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="69c70-194">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="69c70-195">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="69c70-195">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="69c70-196">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="69c70-196">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
