---
title: Tlbexp.exe (類型程式庫匯出工具)
description: Tlbexp.exe，請參閱類型程式庫匯出工具。 此工具會產生類型程式庫，以描述 common language runtime （CLR）元件中定義的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
ms.openlocfilehash: 3cfaa83590fefe31c437d2ff607fb579aec1da61
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517031"
---
# <a name="tlbexpexe-type-library-exporter"></a><span data-ttu-id="dd6e0-104">Tlbexp.exe (類型程式庫匯出工具)</span><span class="sxs-lookup"><span data-stu-id="dd6e0-104">Tlbexp.exe (Type Library Exporter)</span></span>
<span data-ttu-id="dd6e0-105">類型程式庫匯出工具可以產生類型程式庫，這個類型程式庫描述定義在通用語言執行平台組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-105">The Type Library Exporter generates a type library that describes the types defined in a common language runtime assembly.</span></span>  
  
 <span data-ttu-id="dd6e0-106">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="dd6e0-107">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="dd6e0-108">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="dd6e0-109">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="dd6e0-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd6e0-110">語法</span><span class="sxs-lookup"><span data-stu-id="dd6e0-110">Syntax</span></span>  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd6e0-111">參數</span><span class="sxs-lookup"><span data-stu-id="dd6e0-111">Parameters</span></span>  
  
|<span data-ttu-id="dd6e0-112">引數</span><span class="sxs-lookup"><span data-stu-id="dd6e0-112">Argument</span></span>|<span data-ttu-id="dd6e0-113">說明</span><span class="sxs-lookup"><span data-stu-id="dd6e0-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="dd6e0-114">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="dd6e0-114">*assemblyName*</span></span>|<span data-ttu-id="dd6e0-115">要匯出類型程式庫的組件。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-115">The assembly for which to export a type library.</span></span>|  
  
|<span data-ttu-id="dd6e0-116">選項</span><span class="sxs-lookup"><span data-stu-id="dd6e0-116">Option</span></span>|<span data-ttu-id="dd6e0-117">說明</span><span class="sxs-lookup"><span data-stu-id="dd6e0-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dd6e0-118">**/asmpath：** *directory*</span><span class="sxs-lookup"><span data-stu-id="dd6e0-118">**/asmpath:** *directory*</span></span>|<span data-ttu-id="dd6e0-119">指定要搜尋組件的位置。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-119">Specifies the location to search for assemblies.</span></span> <span data-ttu-id="dd6e0-120">如果使用這個選項，則必須明確指定要搜尋參考組件的位置，包括目前的目錄在內。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-120">If you use this option, you must explicitly specify the locations to search for referenced assemblies, including the current directory.</span></span><br /><br /> <span data-ttu-id="dd6e0-121">當您使用 **asmpath** 選項時，型別程式庫匯出工具不會在全域組件快取 (GAC) 中尋找組件。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-121">When you use the **asmpath** option, the Type Library Exporter will not look for an assembly in the global assembly cache (GAC).</span></span>|  
|<span data-ttu-id="dd6e0-122">**/help**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-122">**/help**</span></span>|<span data-ttu-id="dd6e0-123">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="dd6e0-124">**/names:** *filename*</span><span class="sxs-lookup"><span data-stu-id="dd6e0-124">**/names:** *filename*</span></span>|<span data-ttu-id="dd6e0-125">指定類型程式庫中名稱的大小寫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-125">Specifies the capitalization of names in a type library.</span></span> <span data-ttu-id="dd6e0-126">*filename* 引數是一個文字檔。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-126">The *filename* argument is a text file.</span></span> <span data-ttu-id="dd6e0-127">檔案中的每一行指定了類型程式庫中一個名稱的大小寫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-127">Each line in the file specifies the capitalization of one name in the type library.</span></span>|  
|<span data-ttu-id="dd6e0-128">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-128">**/nologo**</span></span>|<span data-ttu-id="dd6e0-129">隱藏 Microsoft 程式啟始資訊顯示。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-129">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="dd6e0-130">**/oldnames**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-130">**/oldnames**</span></span>|<span data-ttu-id="dd6e0-131">在發生類型名稱衝突時，強制 Tlbexp.exe 匯出裝飾類型名稱。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-131">Forces Tlbexp.exe to export decorated type names if there is a type name conflict.</span></span> <span data-ttu-id="dd6e0-132">請注意，此為 .NET Framework 2.0 版之前版本中的預設行為。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-132">Note that this was the default behavior in versions prior to the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="dd6e0-133">**/out:** *file*</span><span class="sxs-lookup"><span data-stu-id="dd6e0-133">**/out:** *file*</span></span>|<span data-ttu-id="dd6e0-134">指定要產生的類型程式庫檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-134">Specifies the name of the type library file to generate.</span></span> <span data-ttu-id="dd6e0-135">如果省略這個選項，Tlbexp.exe 會產生一個與組件名稱 (指實際組件名稱，不一定和包含組件的檔案同名) 相同的類型程式庫和 .tlb 副檔名。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-135">If you omit this option, Tlbexp.exe generates a type library with the same name as the assembly (the actual assembly name, which might not necessarily be the same as the file containing the assembly) and a .tlb extension.</span></span>|  
|<span data-ttu-id="dd6e0-136">**/silence:** `warningnumber`</span><span class="sxs-lookup"><span data-stu-id="dd6e0-136">**/silence:** `warningnumber`</span></span>|<span data-ttu-id="dd6e0-137">隱藏顯示指定的警告。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-137">Suppresses the display of the specified warning.</span></span> <span data-ttu-id="dd6e0-138">此選項無法搭配 **/silent** 使用。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-138">This option cannot be used with **/silent**.</span></span>|  
|<span data-ttu-id="dd6e0-139">**/silent**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-139">**/silent**</span></span>|<span data-ttu-id="dd6e0-140">隱藏顯示成功訊息。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-140">Suppresses the display of success messages.</span></span> <span data-ttu-id="dd6e0-141">此選項無法搭配 **/silence** 使用。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-141">This option cannot be used with **/silence**.</span></span>|  
|<span data-ttu-id="dd6e0-142">**/tlbreference:** *typelibraryname*</span><span class="sxs-lookup"><span data-stu-id="dd6e0-142">**/tlbreference:** *typelibraryname*</span></span>|<span data-ttu-id="dd6e0-143">強制 Tlbexp.exe 明確解析類型程式庫參考，而不需查閱登錄。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-143">Forces Tlbexp.exe to explicitly resolve type library references without consulting the registry.</span></span> <span data-ttu-id="dd6e0-144">例如，如果組件 B 參考組件 A，您就可以使用這個選項提供明確的類型程式庫參考，而不需依賴登錄中所指定的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-144">For example, if assembly B references assembly A, you can use this option to provide an explicit type library reference, rather than relying on the type library specified in the registry.</span></span> <span data-ttu-id="dd6e0-145">Tlbexp.exe 會執行版本檢查，以確定類型程式庫版本是否與組件版本相符；如果不符，便會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-145">Tlbexp.exe performs a version check to ensure that the type library version matches the assembly version; otherwise, it generates an error.</span></span><br /><br /> <span data-ttu-id="dd6e0-146">請注意，如果將 <xref:System.Runtime.InteropServices.ComImportAttribute> 屬性套用至介面，然後又由其他類型實作，則 **tlbreference** 選項仍然會查閱登錄。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-146">Note that the **tlbreference** option still consults the registry in cases where the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute is applied to an interface that is then implemented by another type.</span></span>|  
|<span data-ttu-id="dd6e0-147">**/tlbrefpath:** *path*</span><span class="sxs-lookup"><span data-stu-id="dd6e0-147">**/tlbrefpath:** *path*</span></span>|<span data-ttu-id="dd6e0-148">參考類型程式庫的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-148">Fully qualified path to a referenced type library.</span></span>|  
|<span data-ttu-id="dd6e0-149">**/win32**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-149">**/win32**</span></span>|<span data-ttu-id="dd6e0-150">在 64 位元電腦上編譯時，這個選項會指定 Tlbexp.exe 產生 32 位元的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-150">When compiling on a 64-bit computer, this option specifies that Tlbexp.exe generates a 32-bit type library.</span></span>|  
|<span data-ttu-id="dd6e0-151">**/win64**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-151">**/win64**</span></span>|<span data-ttu-id="dd6e0-152">在 32 位元電腦上編譯時，這個選項會指定 Tlbexp.exe 產生 64 位元的型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-152">When compiling on a 32-bit computer, this option specifies that Tlbexp.exe generates a 64-bit type library.</span></span>|  
|<span data-ttu-id="dd6e0-153">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-153">**/verbose**</span></span>|<span data-ttu-id="dd6e0-154">指定詳細資訊模式，顯示需要產生類型程式庫的任何參考組件的清單。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-154">Specifies verbose mode; displays a list of any referenced assemblies for which a type library needs to be generated.</span></span>|  
|<span data-ttu-id="dd6e0-155">**/?**</span><span class="sxs-lookup"><span data-stu-id="dd6e0-155">**/?**</span></span>|<span data-ttu-id="dd6e0-156">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-156">Displays command syntax and options for the tool.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="dd6e0-157">Tlbexp.exe 的命令列選項不區分大小寫，而且可以依任何順序提供。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-157">The command-line options for Tlbexp.exe are case-insensitive and can be supplied in any order.</span></span> <span data-ttu-id="dd6e0-158">您只需要指定足夠的選項來唯一識別它。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-158">You only need to specify enough of the option to uniquely identify it.</span></span> <span data-ttu-id="dd6e0-159">例如，**/n** 相當於 **/nologo**，且 **/o:** *outfile.tlb* 相當於 **/out:** *outfile.tlb*。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-159">For example, **/n** is equivalent to **/nologo**, and **/o:** *outfile.tlb* is equivalent to **/out:** *outfile.tlb*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd6e0-160">備註</span><span class="sxs-lookup"><span data-stu-id="dd6e0-160">Remarks</span></span>  
 <span data-ttu-id="dd6e0-161">Tlbexp.exe 會產生一個類型程式庫，其含有組件中所定義的類型定義。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-161">Tlbexp.exe generates a type library that contains definitions of the types defined in the assembly.</span></span> <span data-ttu-id="dd6e0-162">應用程式 (例如 Visual Basic 6.0) 可以使用產生的類型程式庫來繫結至組件中所定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-162">Applications such as Visual Basic 6.0 can use the generated type library to bind to the .NET types defined in the assembly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dd6e0-163">您無法使用 Tlbexp.exe 匯出 Windows 中繼資料 (.winmd) 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-163">You cannot use Tlbexp.exe to export Windows metadata (.winmd) files.</span></span> <span data-ttu-id="dd6e0-164">不支援匯出 Windows 執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-164">Exporting Windows Runtime assemblies is not supported.</span></span>  
  
 <span data-ttu-id="dd6e0-165">全部組件會一次同時轉換。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-165">The entire assembly is converted at once.</span></span> <span data-ttu-id="dd6e0-166">您無法使用 Tlbexp.exe 來為組件中所定義的類型子集產生類型資訊。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-166">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
 <span data-ttu-id="dd6e0-167">您無法使用 Tlbexp.exe 從已經使用[型別程式庫匯入工具 (Tlbimp.exe)](tlbimp-exe-type-library-importer.md) 匯入的組件中產生型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-167">You cannot use Tlbexp.exe to produce a type library from an assembly that was imported using the [Type Library Importer (Tlbimp.exe)](tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="dd6e0-168">反之，您應該參考使用 Tlbimp.exe 匯入的原始類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-168">Instead, you should refer to the original type library that was imported with Tlbimp.exe.</span></span> <span data-ttu-id="dd6e0-169">您可以從參考使用 Tlbimp.exe 匯入之組件的組件匯出類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-169">You can export a type library from an assembly that references assemblies that were imported using Tlbimp.exe.</span></span> <span data-ttu-id="dd6e0-170">請參閱下列範例區段。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-170">See the examples section below.</span></span>  
  
 <span data-ttu-id="dd6e0-171">Tlbexp.exe 會將產生的類型程式庫放置在目前的工作目錄或指定給輸出檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-171">Tlbexp.exe places generated type libraries in the current working directory or the directory specified for the output file.</span></span> <span data-ttu-id="dd6e0-172">單一組件可能導致產生多個類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-172">A single assembly might cause several type libraries to be generated.</span></span>  
  
 <span data-ttu-id="dd6e0-173">Tlbexp.exe 會產生類型程式庫但是不會註冊它。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-173">Tlbexp.exe generates a type library but does not register it.</span></span> <span data-ttu-id="dd6e0-174">這和[組件註冊工具 (Regasm.exe)](regasm-exe-assembly-registration-tool.md) 形成對比，組件註冊工具會產生並註冊型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-174">This is in contrast to the [Assembly Registration tool (Regasm.exe)](regasm-exe-assembly-registration-tool.md), which both generates and registers a type library.</span></span> <span data-ttu-id="dd6e0-175">若要產生並以 COM 註冊類型程式庫，請使用 Regasm.exe。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-175">To generate and register a type library with COM, use Regasm.exe.</span></span>  
  
 <span data-ttu-id="dd6e0-176">如果您未指定 `/win32` 或 `/win64` 選項當中的任一項，Tlbexp.exe 會產生與執行編譯的電腦類型 (32 位元或 64 位元電腦) 相對應之 32 位元或 64 位元的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-176">If you do not specify either the `/win32` or `/win64` option, Tlbexp.exe generates a 32-bit or 64-bit type library that corresponds to the type of computer on which you are performing the compilation (32-bit or 64-bit computer).</span></span> <span data-ttu-id="dd6e0-177">為了交互編譯，您可以在 32 位元電腦上使用 `/win64` 選項以產生 64 位元的類型程式庫，或在 64 位元電腦上使用 `/win32` 選項以產生 32 位元的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-177">For cross-compilation purposes, you can use the `/win64` option on a 32-bit computer to generate a 64-bit type library and you can use the `/win32` option on a 64-bit computer to generate a 32-bit type library.</span></span> <span data-ttu-id="dd6e0-178">在 32 位元的類型程式庫中，<xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 值會設定為 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-178">In 32-bit type libraries, the <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> value is set to <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>.</span></span> <span data-ttu-id="dd6e0-179">在 64 位元的型別程式庫中，<xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 值會設定為 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-179">In 64-bit type libraries, the <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> value is set to <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>.</span></span> <span data-ttu-id="dd6e0-180">所有資料類型的轉換資料 (例如，類似 `IntPtr` 和 `UIntPtr` 指標大小的資料類型) 都會適當地加以轉換。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-180">All data type transformations (for example, pointer-sized data types such as `IntPtr` and `UIntPtr`) are converted appropriately.</span></span>  
  
 <span data-ttu-id="dd6e0-181">如果您使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性來指定 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> 或 `VT_UNKOWN` 的 `VT_DISPATCH` 值，則 Tlbexp.exe 會忽略所有後續使用的 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> 欄位。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-181">If you use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> value of `VT_UNKOWN` or `VT_DISPATCH`, Tlbexp.exe ignores any subsequent use of the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> field.</span></span> <span data-ttu-id="dd6e0-182">例如，假設有以下的簽章：</span><span class="sxs-lookup"><span data-stu-id="dd6e0-182">For example, given the following signatures:</span></span>  
  
```csharp
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 <span data-ttu-id="dd6e0-183">會產生下列類型程式庫：</span><span class="sxs-lookup"><span data-stu-id="dd6e0-183">the following type library is generated:</span></span>  
  
```cpp
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 <span data-ttu-id="dd6e0-184">請注意，Tlbexp.exe 會忽略 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> 欄位。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-184">Note that Tlbexp.exe ignores the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> field.</span></span>  
  
 <span data-ttu-id="dd6e0-185">由於類型程式庫無法容納這些組件中的所有資訊，因此，Tlbexp.exe 在匯出處理序時可能會捨棄一些資料。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-185">Because type libraries cannot accommodate all the information found in assemblies, Tlbexp.exe might discard some data during the export process.</span></span> <span data-ttu-id="dd6e0-186">如需轉換處理序的說明並且識別型別程式庫所發出每件資訊的來源，請參閱[組件至型別程式庫轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-186">For an explanation of the transformation process and identification of the source of each piece of information emitted to a type library, see the [Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).</span></span>  
  
 <span data-ttu-id="dd6e0-187">請注意，類型程式庫匯出工具會將 <xref:System.TypedReference> 參數匯出為 `VARIANT` 的方法，即使 <xref:System.TypedReference> 物件在 Unmanaged 程式碼中不具任何意義。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-187">Note that the Type Library Exporter exports methods that have <xref:System.TypedReference> parameters as `VARIANT`, even though the <xref:System.TypedReference> object has no meaning in unmanaged code.</span></span> <span data-ttu-id="dd6e0-188">當您匯出具有 <xref:System.TypedReference> 參數的方法時，類型程式庫匯出工具不會產生警告或錯誤，而使用結果類型程式庫的 Unmanaged 程式碼也將無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-188">When you export methods that have <xref:System.TypedReference> parameters, the Type Library Exporter will not generate a warning or error and unmanaged code that uses the resulting type library will not run properly.</span></span>  
  
 <span data-ttu-id="dd6e0-189">Microsoft Windows 2000 (含) 以後版本都支援類型程式庫匯出工具。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-189">The Type Library Exporter is supported on Microsoft Windows 2000 and later.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dd6e0-190">範例</span><span class="sxs-lookup"><span data-stu-id="dd6e0-190">Examples</span></span>  
 <span data-ttu-id="dd6e0-191">下列命令會產生一個和 `myTest.dll` 中組件同名的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-191">The following command generates a type library with the same name as the assembly found in `myTest.dll`.</span></span>  
  
```console  
tlbexp myTest.dll  
```  
  
 <span data-ttu-id="dd6e0-192">下列命令會以 `clipper.tlb` 名稱產生類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-192">The following command generates a type library with the name `clipper.tlb`.</span></span>  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 <span data-ttu-id="dd6e0-193">下列命令說明使用 Tlbexp.exe 來從組件 (其參考已經使用 Tlbimp.exe 匯入的組件) 中匯出類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-193">The following example illustrates using Tlbexp.exe to export a type library from an assembly that references assemblies that were imported using Tlbimp.exe.</span></span>  
  
 <span data-ttu-id="dd6e0-194">先使用 Tlbimp.exe 匯入 `myLib.tlb` 類型程式庫，然後將它儲存為 `myLib.dll`。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-194">First use Tlbimp.exe to import the type library `myLib.tlb` and save it as `myLib.dll`.</span></span>  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 <span data-ttu-id="dd6e0-195">下列命令會使用 C# 編譯器來編譯 `Sample.dll,`，它會參考上一個範例中所建立的 `myLib.dll`。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-195">The following command uses the C# compiler to compile the `Sample.dll,` which references `myLib.dll` created in the previous example.</span></span>  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 <span data-ttu-id="dd6e0-196">下列命令會產生參考 `Sample.dll` 之類型程式庫的 `myLib.dll`。</span><span class="sxs-lookup"><span data-stu-id="dd6e0-196">The following command generates a type library for `Sample.dll` that references `myLib.dll`.</span></span>  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd6e0-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd6e0-197">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [<span data-ttu-id="dd6e0-198">工具</span><span class="sxs-lookup"><span data-stu-id="dd6e0-198">Tools</span></span>](index.md)
- [<span data-ttu-id="dd6e0-199">Regasm.exe （元件註冊工具）</span><span class="sxs-lookup"><span data-stu-id="dd6e0-199">Regasm.exe (Assembly Registration Tool)</span></span>](regasm-exe-assembly-registration-tool.md)
- <span data-ttu-id="dd6e0-200">[組件至型別程式庫轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dd6e0-200">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>
- [<span data-ttu-id="dd6e0-201">Tlbimp.exe （類型程式庫匯入工具）</span><span class="sxs-lookup"><span data-stu-id="dd6e0-201">Tlbimp.exe (Type Library Importer)</span></span>](tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="dd6e0-202">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="dd6e0-202">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
