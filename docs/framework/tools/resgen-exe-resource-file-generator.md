---
title: Resgen.exe (資源檔產生器)
description: 使用資源檔產生器 Resgen.exe。 將文字（.txt、.restext）和 XML 資源格式（.resx）檔案轉換為可內嵌 CLR 執行時間二進位檔（.resources）。
ms.date: 03/30/2017
helpviewer_keywords:
- resource files, .resources files
- resource files, .resx files
- resx files (resource files)
- .resources files
- files, converting
- Resource File Generator
- .resx files
- Resgen.exe
- resource files, converting
- converting files, Resource File Generator
- binary resources files
- embedding files in runtime binary executable
ms.assetid: 8ef159de-b660-4bec-9213-c3fbc4d1c6f4
ms.openlocfilehash: f51ee6c8537abafc82017f3cc29d734e939a254f
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517226"
---
# <a name="resgenexe-resource-file-generator"></a><span data-ttu-id="6f1e1-104">Resgen.exe (資源檔產生器)</span><span class="sxs-lookup"><span data-stu-id="6f1e1-104">Resgen.exe (Resource File Generator)</span></span>
<span data-ttu-id="6f1e1-105">資源檔產生器 (Resgen.exe) 可以將文字檔 (.txt 或 .restext) 及 XML 架構資源格式檔 (.resx)，轉換成通用語言執行平台二進位檔 (.resources)，這種檔案可以嵌入至執行階段二進位可執行檔或附屬組件 </span><span class="sxs-lookup"><span data-stu-id="6f1e1-105">The Resource File Generator (Resgen.exe) converts text (.txt or .restext) files and XML-based resource format (.resx) files to common language runtime binary (.resources) files that can be embedded in a runtime binary executable or satellite assembly.</span></span> <span data-ttu-id="6f1e1-106">(請參閱[建立資源檔](../resources/creating-resource-files-for-desktop-apps.md))。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-106">(See [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).)</span></span>  
  
 <span data-ttu-id="6f1e1-107">Resgen.exe 為執行下列工作的通用資源轉換公用程式：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-107">Resgen.exe is a general-purpose resource conversion utility that performs the following tasks:</span></span>  
  
- <span data-ttu-id="6f1e1-108">將 .txt 或 .restext 檔轉換成 .resources 或 .resx 檔 </span><span class="sxs-lookup"><span data-stu-id="6f1e1-108">Converts .txt or .restext files to .resources or .resx files.</span></span> <span data-ttu-id="6f1e1-109">(.restext 檔案的格式與 .txt 檔案的格式相同。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-109">(The format of .restext files is identical to the format of .txt files.</span></span> <span data-ttu-id="6f1e1-110">不過，.restext 副檔名可以幫助您更容易識別內含資源定義的文字檔)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-110">However, the .restext extension helps you identify text files that contain resource definitions more easily.)</span></span>  
  
- <span data-ttu-id="6f1e1-111">將 .resources 檔轉換成文字或 .resx 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-111">Converts .resources files to text or .resx files.</span></span>  
  
- <span data-ttu-id="6f1e1-112">將 .resx 檔轉換成文字或 .resources 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-112">Converts .resx files to text or .resources files.</span></span>  
  
- <span data-ttu-id="6f1e1-113">將字串資源從元件解壓縮到適用于 Windows 8.x 存放區應用程式的 .resw 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-113">Extracts the string resources from an assembly into a .resw file that is suitable for use in a Windows 8.x Store app.</span></span>  
  
- <span data-ttu-id="6f1e1-114">建立可存取個別具名資源和對於 <xref:System.Resources.ResourceManager> 執行個體的強類型類別。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-114">Creates a strongly typed class that provides access to individual named resources and to the <xref:System.Resources.ResourceManager> instance.</span></span>  
  
 <span data-ttu-id="6f1e1-115">如果 Resgen.exe 因任何理由而失敗，則傳回值將會是 –1。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-115">If Resgen.exe fails for any reason, the return value is –1.</span></span>  
  
 <span data-ttu-id="6f1e1-116">若要取得 Resgen.exe 的協助，您可以使用下列命令（未指定任何選項）來顯示 Resgen.exe 的命令語法和選項：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-116">To get help with Resgen.exe, you can use the following command, with no options specified, to display the command syntax and options for Resgen.exe:</span></span>  
  
```console  
resgen  
```  
  
 <span data-ttu-id="6f1e1-117">您也可以使用 `/?` 參數：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-117">You can also use the `/?` switch:</span></span>  
  
```console  
resgen /?  
```  
  
 <span data-ttu-id="6f1e1-118">如果您使用 Resgen.exe 產生二進位 .resources 檔，您可以使用語言編譯器將二進位檔案內嵌至可執行檔元件，或使用[元件連結器（Al.exe）](al-exe-assembly-linker.md)將它們編譯成附屬元件。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-118">If you use Resgen.exe to generate binary .resources files, you can use a language compiler to embed the binary files into executable assemblies, or you can use the [Assembly Linker (Al.exe)](al-exe-assembly-linker.md) to compile them into satellite assemblies.</span></span>  
  
 <span data-ttu-id="6f1e1-119">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-119">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6f1e1-120">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-120">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6f1e1-121">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-121">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="6f1e1-122">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-122">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f1e1-123">語法</span><span class="sxs-lookup"><span data-stu-id="6f1e1-123">Syntax</span></span>  
  
```console  
resgen  [-define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f1e1-124">參數</span><span class="sxs-lookup"><span data-stu-id="6f1e1-124">Parameters</span></span>  
  
|<span data-ttu-id="6f1e1-125">參數</span><span class="sxs-lookup"><span data-stu-id="6f1e1-125">Parameter or switch</span></span>|<span data-ttu-id="6f1e1-126">說明</span><span class="sxs-lookup"><span data-stu-id="6f1e1-126">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="6f1e1-127">`/define:` *symbol1*[, *symbol2*,...]</span><span class="sxs-lookup"><span data-stu-id="6f1e1-127">`/define:` *symbol1*[, *symbol2*,...]</span></span>|<span data-ttu-id="6f1e1-128">從 .NET Framework 4.5 開始，支援文字資源檔 (.txt 或 .restext) 的條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-128">Starting with the .NET Framework 4.5, supports conditional compilation in text-based (.txt or .restext) resource files.</span></span> <span data-ttu-id="6f1e1-129">如果 *symbol* 對應至在 `#ifdef` 建構內輸入文字檔中的符號，關聯字串資源會包含在 .resources 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-129">If *symbol* corresponds to a symbol included in the input text file within a `#ifdef` construct, the associated string resource is included in the .resources file.</span></span> <span data-ttu-id="6f1e1-130">如果輸入文字檔包含有不是 `#if !` 參數所定義之符號的 `/define` 陳述式，關聯的字串資源會包含在資源檔中。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-130">If the input text file includes an `#if !` statement with a symbol that is not defined by the `/define` switch, the associated string resource is included in the resources file.</span></span><br /><br /> <span data-ttu-id="6f1e1-131">使用非文字檔案則會忽略 `/define`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-131">`/define` is ignored if it is used with non-text files.</span></span> <span data-ttu-id="6f1e1-132">符號會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-132">Symbols are case-sensitive.</span></span><br /><br /> <span data-ttu-id="6f1e1-133">如需這個選項的詳細資訊，請參閱本主題稍後的[條件式編譯資源](#Conditional)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-133">For more information about this option, see [Conditionally Compiling Resources](#Conditional) later in this topic.</span></span>|  
|`useSourcePath`|<span data-ttu-id="6f1e1-134">具體指明輸入檔的目前目錄是用來解析相對檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-134">Specifies that the input file's current directory is to be used to resolve relative file paths.</span></span>|  
|`/compile`|<span data-ttu-id="6f1e1-135">可讓您指定在單一大量作業中，將多個 .resx 或文字檔轉換成多個 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-135">Enables you to specify multiple .resx or text files to convert to multiple .resources files in a single bulk operation.</span></span> <span data-ttu-id="6f1e1-136">如果您不指定這個選項，則只能指定一個輸入檔引數。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-136">If you do not specify this option, you can specify only one input file argument.</span></span> <span data-ttu-id="6f1e1-137">輸出檔案的名稱為 <檔案名稱>\*\*.resources。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-137">Output files are named *filename*.resources.</span></span><br /><br /> <span data-ttu-id="6f1e1-138">這個選項無法與 `/str:` 選項搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-138">This option cannot be used with the `/str:` option.</span></span><br /><br /> <span data-ttu-id="6f1e1-139">如需這個選項的詳細資訊，請參閱本主題稍後的[編譯或轉換多個檔案](#Multiple)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-139">For more information about this option, see [Compiling or Converting Multiple Files](#Multiple) later in this topic.</span></span>|  
|<span data-ttu-id="6f1e1-140">`/r:` `assembly`</span><span class="sxs-lookup"><span data-stu-id="6f1e1-140">`/r:` `assembly`</span></span>|<span data-ttu-id="6f1e1-141">從指定的組件參考中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-141">References metadata from the specified assembly.</span></span> <span data-ttu-id="6f1e1-142">在轉換 .resx 檔時，以及讓 Resgen.exe 序列化或還原序列化物件資源時使用。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-142">It is used when converting .resx files and allows Resgen.exe to serialize or deserialize object resources.</span></span> <span data-ttu-id="6f1e1-143">它類似 C# 和 Visual Basic 編譯器的 `/reference:` 或 `/r:` 選項。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-143">It is similar to the `/reference:` or `/r:` options for the C# and Visual Basic compilers.</span></span>|  
|`filename.extension`|<span data-ttu-id="6f1e1-144">指定要轉換的輸入檔名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-144">Specifies the name of the input file to convert.</span></span> <span data-ttu-id="6f1e1-145">如果您使用的是這個資料表前的命令列語法中的第一個、較長者，`extension` 必須是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-145">If you're using the first, lengthier command-line syntax presented before this table,  `extension` must be one of the following:</span></span><br /><br /> <span data-ttu-id="6f1e1-146">.txt 或 .restext</span><span class="sxs-lookup"><span data-stu-id="6f1e1-146">.txt or .restext</span></span><br /> <span data-ttu-id="6f1e1-147">要轉換成 .resources 或 .resx 檔的文字檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-147">A text file to convert to a .resources or a .resx file.</span></span> <span data-ttu-id="6f1e1-148">文字檔只能包含字串資源。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-148">Text files can contain only string resources.</span></span> <span data-ttu-id="6f1e1-149">如需檔案格式的詳細資訊，請參閱[建立資源檔](../resources/creating-resource-files-for-desktop-apps.md)的＜文字檔中的資源＞一節。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-149">For information about the file format, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).</span></span><br /><br /> <span data-ttu-id="6f1e1-150">.resx</span><span class="sxs-lookup"><span data-stu-id="6f1e1-150">.resx</span></span><br /> <span data-ttu-id="6f1e1-151">要轉換成 .resources 或文字檔 (.txt 或 .restext) 的 XML 架構資源檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-151">An XML-based resource file to convert to a .resources or a text (.txt or .restext) file.</span></span><br /><br /> <span data-ttu-id="6f1e1-152">.resources</span><span class="sxs-lookup"><span data-stu-id="6f1e1-152">.resources</span></span><br /> <span data-ttu-id="6f1e1-153">要轉換成 .resx 或文字檔 (.txt 或 .restext) 的二進位資源檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-153">A binary resource file to convert to a .resx or a text (.txt or .restext) file.</span></span><br /><br /> <span data-ttu-id="6f1e1-154">如果您使用的是這個資料表前的命令列語法中的第二個、較短者，`extension` 必須為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-154">If you're using the second, shorter command-line syntax presented before this table, `extension` must be the following:</span></span><br /><br /> <span data-ttu-id="6f1e1-155">.exe 或 .dll。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-155">.exe or .dll</span></span><br /> <span data-ttu-id="6f1e1-156">.NET Framework 元件（可執行檔或程式庫），其字串資源會解壓縮至 .resw 檔案，以用於開發 Windows 8.x 存放區應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-156">A .NET Framework assembly (executable or library) whose string resources are to be extracted to a .resw file for use in developing Windows 8.x Store apps.</span></span>|  
|`outputFilename.extension`|<span data-ttu-id="6f1e1-157">指定要建立之資源檔的名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-157">Specifies the name and type of the resource file to create.</span></span><br /><br /> <span data-ttu-id="6f1e1-158">從 .txt、.restext 或 .resx 檔案轉換至 .resource 檔時，這是選擇性的引數。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-158">This argument is optional when converting from a .txt, .restext, or .resx file to a .resources file.</span></span> <span data-ttu-id="6f1e1-159">如果沒有指定 `outputFilename`，Resgen.exe 會將 .resources 副檔名附加至輸入 `filename` 中，並且將檔案寫入包含 `filename,extension` 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-159">If you do not specify `outputFilename`, Resgen.exe appends a .resources extension to the input `filename` and writes the file to the directory that contains `filename,extension`.</span></span><br /><br /> <span data-ttu-id="6f1e1-160">從 .resources 檔轉換時，`outputFilename.extension` 是強制的引數。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-160">The `outputFilename.extension` argument is mandatory when converting from a .resources file.</span></span> <span data-ttu-id="6f1e1-161">在將 .resources 檔轉換成 XML 架構資源檔時指定檔案名稱及 .resx 副檔名。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-161">Specify a file name with the .resx extension when converting a .resources file to an XML-based resource file.</span></span> <span data-ttu-id="6f1e1-162">將 .resources 檔案轉換成文字檔時，指定檔案名稱及 .txt 或 .restext 副檔名。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-162">Specify a file name with the .txt or .restext extension when converting a .resources file to a text file.</span></span> <span data-ttu-id="6f1e1-163">當 .resources 檔只包含字串值時，您應將 .resources 檔轉換成 .txt 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-163">You should convert a .resources file to a .txt file only when the .resources file contains only string values.</span></span>|  
|`outputDirectory`|<span data-ttu-id="6f1e1-164">對於 Windows 8.x 存放區應用程式，會指定要在其中寫入包含字串資源之 .resw 檔案的目錄 `filename.extension` 。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-164">For Windows 8.x Store apps, specifies the directory in which a .resw file that contains the string resources in `filename.extension` will be written.</span></span> <span data-ttu-id="6f1e1-165">`outputDirectory` 必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-165">`outputDirectory` must already exist.</span></span>|  
|<span data-ttu-id="6f1e1-166">`/str:` `language[,namespace[,classname[,filename]]]`</span><span class="sxs-lookup"><span data-stu-id="6f1e1-166">`/str:` `language[,namespace[,classname[,filename]]]`</span></span>|<span data-ttu-id="6f1e1-167">以 `language` 選項所指定的程式設計語言建立強類型資源類別檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-167">Creates a strongly typed resource class file in the programming language specified in the `language` option.</span></span> <span data-ttu-id="6f1e1-168">`language` 可包含下列其中一種常值：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-168">`language` can consist of one of the following literals:</span></span><br /><br /> <span data-ttu-id="6f1e1-169">-   C#：`c#`、`cs` 或 `csharp`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-169">-   For C#: `c#`, `cs`, or `csharp`.</span></span><br /><span data-ttu-id="6f1e1-170">-   Visual Basic：`vb` 或 `visualbasic`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-170">-   For Visual Basic: `vb` or `visualbasic`.</span></span><br /><span data-ttu-id="6f1e1-171">-   VBScript：`vbs` 或 `vbscript`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-171">-   For VBScript: `vbs` or `vbscript`.</span></span><br /><span data-ttu-id="6f1e1-172">-   C++：`c++`、`mc` 或 `cpp`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-172">-   For C++: `c++`, `mc`, or `cpp`.</span></span><br /><span data-ttu-id="6f1e1-173">-   JavaScript：`js`、`jscript` 或 `javascript`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-173">-   For JavaScript: `js`, `jscript`, or `javascript`.</span></span><br /><br /> <span data-ttu-id="6f1e1-174">您可以使用 `namespace` 選項指定專案的預設命名空間，使用 `classname` 選項指定所產生類別的名稱，以及使用 `filename` 選項指定類別檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-174">The `namespace` option specifies the project's default namespace, the `classname` option specifies the name of the generated class, and the `filename` option specifies the name of the class file.</span></span><br /><br /> <span data-ttu-id="6f1e1-175">`/str:` 選項只允許一個輸入檔，因此無法搭配 `/compile` 選項使用。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-175">The `/str:` option allows only one input file, so it cannot be used with the `/compile` option.</span></span><br /><br /> <span data-ttu-id="6f1e1-176">如果有指定 `namespace` 但未指定 `classname`，此時類別名稱便會衍生自該輸出檔名稱 (例如，以底線替代句號)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-176">If `namespace` is specified but `classname` is not, the class name is derived from the output file name (for example, underscores are substituted for periods).</span></span> <span data-ttu-id="6f1e1-177">這樣一來，強類型資源可能無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-177">The strongly typed resources might not work correctly as a result.</span></span> <span data-ttu-id="6f1e1-178">若要避免此問題，請同時指定類別名稱和輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-178">To avoid this, specify both class name and output file name.</span></span><br /><br /> <span data-ttu-id="6f1e1-179">如需這個選項的詳細資訊，請參閱本主題稍後的[產生強型別資源類別](#Strong)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-179">For more information about this option, see [Generating a Strongly Typed Resource Class](#Strong) later in this topic.</span></span>|  
|`/publicClass`|<span data-ttu-id="6f1e1-180">建立強類型資源類別做為公用類別。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-180">Creates a strongly typed resource class as a public class.</span></span> <span data-ttu-id="6f1e1-181">根據預設，資源類別是在 C# 中的 `internal` 和 Visual Basic 中的 `Friend`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-181">By default, the resource class is `internal` in C# and `Friend` in Visual Basic.</span></span><br /><br /> <span data-ttu-id="6f1e1-182">如果沒有使用 `/str:` 選項，則會忽略這個選項。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-182">This option is ignored if the `/str:` option is not used.</span></span>|  
  
## <a name="resgenexe-and-resource-file-types"></a><span data-ttu-id="6f1e1-183">Resgen.exe 和資源檔類型</span><span class="sxs-lookup"><span data-stu-id="6f1e1-183">Resgen.exe and Resource File Types</span></span>  
 <span data-ttu-id="6f1e1-184">要成功地用 Resgen.exe 轉換資源，文字檔和 .resx 檔必須遵守正確格式。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-184">In order for Resgen.exe to successfully convert resources, text and .resx files must follow the correct format.</span></span>  
  
### <a name="text-txt-and-restext-files"></a><span data-ttu-id="6f1e1-185">文字檔 (.txt 和 .restext)</span><span class="sxs-lookup"><span data-stu-id="6f1e1-185">Text (.txt and .restext) Files</span></span>  
 <span data-ttu-id="6f1e1-186">文字檔 (.txt 或 .restext) 只能包含字串資源。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-186">Text (.txt or .restext) files may contain only string resources.</span></span> <span data-ttu-id="6f1e1-187">如果您所撰寫的應用程式必須將字串轉譯成多種語言，字串資源是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-187">String resources are useful if you are writing an application that must have strings translated into several languages.</span></span> <span data-ttu-id="6f1e1-188">例如，使用適當的字串資源，您可以輕易地按地區安排功能表字串。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-188">For example, you can easily regionalize menu strings by using the appropriate string resource.</span></span> <span data-ttu-id="6f1e1-189">Resgen.exe 會讀取含有名稱/值組的文字檔，其中名稱是描述資源的字串，而值是資源字串本身。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-189">Resgen.exe reads text files that contain name/value pairs, where the name is a string that describes the resource and the value is the resource string itself.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f1e1-190">如需 .txt 或 .restext 檔格式的詳細資訊，請參閱[建立資源檔](../resources/creating-resource-files-for-desktop-apps.md)的＜文字檔中的資源＞一節。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-190">For information about the format of .txt and .restext files, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).</span></span>  
  
 <span data-ttu-id="6f1e1-191">包含資源的文字檔除非其只包含基本拉丁範圍 (到 U+007F) 內的字元，否則必須以 UTF-8 或 Unicode (UTF-16) 的編碼方式保存。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-191">A text file that contains resources must be saved with UTF-8 or Unicode (UTF-16) encoding unless it contains only characters in the Basic Latin range (to U+007F).</span></span> <span data-ttu-id="6f1e1-192">Resgen.exe 在處理使用 ANSI 編碼方式儲存的文字檔時，會移除延伸的 ANSI 字元。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-192">Resgen.exe removes extended ANSI characters when it processes a text file that is saved using ANSI encoding.</span></span>  
  
 <span data-ttu-id="6f1e1-193">Resgen.exe 會針對重複的資源名稱檢查文字檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-193">Resgen.exe checks the text file for duplicate resource names.</span></span> <span data-ttu-id="6f1e1-194">如果文字檔包含重複的資源名稱，Resgen.exe 將會發出警告並忽略第二個值。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-194">If the text file contains duplicate resource names, Resgen.exe will emit a warning and ignore the second value.</span></span>  
  
### <a name="resx-files"></a><span data-ttu-id="6f1e1-195">.resx 檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-195">.resx Files</span></span>  
 <span data-ttu-id="6f1e1-196">.resx 資源檔格式由 XML 項目組成。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-196">The .resx resource file format consists of XML entries.</span></span> <span data-ttu-id="6f1e1-197">您可以在這些 XML 項目中指定字串資源，就像在文字檔中的方式一樣。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-197">You can specify string resources within these XML entries, as you would in text files.</span></span> <span data-ttu-id="6f1e1-198">.resx 檔優於文字檔的原因，就是您也可以指定或內嵌物件。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-198">A primary advantage of .resx files over text files is that you can also specify or embed objects.</span></span> <span data-ttu-id="6f1e1-199">在檢視 .resx 檔時，您可以實際看到內嵌物件 (如圖片) 的二進位格式 (當這個二進位資訊是資源資訊清單的一部分時)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-199">When you view a .resx file, you can see the binary form of an embedded object (for example, a picture) when this binary information is a part of the resource manifest.</span></span> <span data-ttu-id="6f1e1-200">與文字檔一樣，您可以使用文字編輯器開啟 .resx 檔案 (例如 [記事本] 或 Microsoft Word) 並寫入、剖析和操作其內容。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-200">As with text files, you can open a .resx file with a text editor (such as Notepad or Microsoft Word) and write, parse, and manipulate its contents.</span></span> <span data-ttu-id="6f1e1-201">請注意您必須對 XML 標記和 .resx 檔案結構有相當的認識才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-201">Note that this requires a good knowledge of XML tags and the .resx file structure.</span></span> <span data-ttu-id="6f1e1-202">如需 .resx 檔案格式的詳細資訊，請參閱[建立資源檔](../resources/creating-resource-files-for-desktop-apps.md)＜.resx 檔中的資源＞一節。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-202">For more details on the .resx file format, see the "Resources in .resx Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).</span></span>  
  
 <span data-ttu-id="6f1e1-203">若要建立含有內嵌非字串物件的 .resources 檔，您必須使用 Resgen.exe 來轉換含有物件的 .resx 檔，或使用 <xref:System.Resources.ResourceWriter> 類別提供的方法，直接從程式碼中將物件資源加入您的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-203">In order to create a .resources file that contains embedded nonstring objects, you must either use Resgen.exe to convert a .resx file containing objects or add the object resources to your file directly from code by calling the methods provided by the <xref:System.Resources.ResourceWriter> class.</span></span>  
  
 <span data-ttu-id="6f1e1-204">如果使用 Resgen.exe 將含有物件的 .resx 檔或 .resources 檔轉換成文字檔，則所有字串資源都會正確的轉換，但是非字串物件的資料類型也會以字串的形式寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-204">If your .resx or .resources file contains objects and you use Resgen.exe to convert it to a text file, all the string resources will be converted correctly, but the data types of the nonstring objects will also be written to the file as strings.</span></span> <span data-ttu-id="6f1e1-205">在進行轉換時您將會遺漏內嵌物件，而 Resgen.exe 將會報告擷取資源時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-205">You will lose the embedded objects in the conversion, and Resgen.exe will report that an error occurred in retrieving the resources.</span></span>  
  
### <a name="converting-between-resources-file-types"></a><span data-ttu-id="6f1e1-206">資源檔案類型間的轉換</span><span class="sxs-lookup"><span data-stu-id="6f1e1-206">Converting Between Resources File Types</span></span>  
 <span data-ttu-id="6f1e1-207">當您在不同資源檔類型之間轉換時，根據來源和目標檔案的類型，Resgen.exe 可能無法執行轉換也可能會遺漏特定資源的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-207">When you convert between different resource file types, Resgen.exe may not be able to perform the conversion or may lose information about specific resources, depending on the source and target file types.</span></span> <span data-ttu-id="6f1e1-208">從某種資源檔案類型轉換為另一種類型時，下表指定成功轉換的類型。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-208">The following table specifies the types of conversions that are successful when converting from one resource file type to another.</span></span>  
  
|<span data-ttu-id="6f1e1-209">來源檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-209">Convert from</span></span>|<span data-ttu-id="6f1e1-210">轉至文字檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-210">To text file</span></span>|<span data-ttu-id="6f1e1-211">轉至 .resx 檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-211">To .resx file</span></span>|<span data-ttu-id="6f1e1-212">轉至 .resw 檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-212">To .resw file</span></span>|<span data-ttu-id="6f1e1-213">轉至 .resources 檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-213">To .resources file</span></span>|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|<span data-ttu-id="6f1e1-214">文字檔 (.txt 或 .restext)</span><span class="sxs-lookup"><span data-stu-id="6f1e1-214">Text (.txt or .restext) file</span></span>|--|<span data-ttu-id="6f1e1-215">沒有問題</span><span class="sxs-lookup"><span data-stu-id="6f1e1-215">No issues</span></span>|<span data-ttu-id="6f1e1-216">不支援</span><span class="sxs-lookup"><span data-stu-id="6f1e1-216">Not supported</span></span>|<span data-ttu-id="6f1e1-217">沒有問題</span><span class="sxs-lookup"><span data-stu-id="6f1e1-217">No issues</span></span>|  
|<span data-ttu-id="6f1e1-218">.resx 檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-218">.resx file</span></span>|<span data-ttu-id="6f1e1-219">檔案包含非字串資源 (包括文件連結) 時轉換失敗</span><span class="sxs-lookup"><span data-stu-id="6f1e1-219">Conversion fails if file contains non-string resources (including file links)</span></span>|--|<span data-ttu-id="6f1e1-220">不支援</span><span class="sxs-lookup"><span data-stu-id="6f1e1-220">Not supported</span></span>|<span data-ttu-id="6f1e1-221">沒有問題</span><span class="sxs-lookup"><span data-stu-id="6f1e1-221">No issues</span></span>|  
|<span data-ttu-id="6f1e1-222">.resources 檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-222">.resources file</span></span>|<span data-ttu-id="6f1e1-223">檔案包含非字串資源 (包括文件連結) 時轉換失敗</span><span class="sxs-lookup"><span data-stu-id="6f1e1-223">Conversion fails if file contains non-string resources (including file links)</span></span>|<span data-ttu-id="6f1e1-224">沒有問題</span><span class="sxs-lookup"><span data-stu-id="6f1e1-224">No issues</span></span>|<span data-ttu-id="6f1e1-225">不支援</span><span class="sxs-lookup"><span data-stu-id="6f1e1-225">Not supported</span></span>|--|  
|<span data-ttu-id="6f1e1-226">.exe 或 .dll 組譯碼</span><span class="sxs-lookup"><span data-stu-id="6f1e1-226">.exe or .dll assembly</span></span>|<span data-ttu-id="6f1e1-227">不支援</span><span class="sxs-lookup"><span data-stu-id="6f1e1-227">Not supported</span></span>|<span data-ttu-id="6f1e1-228">不支援</span><span class="sxs-lookup"><span data-stu-id="6f1e1-228">Not supported</span></span>|<span data-ttu-id="6f1e1-229">只有字串資源 (包括路徑名稱) 被當做資源</span><span class="sxs-lookup"><span data-stu-id="6f1e1-229">Only string resources (including path names) are recognized as resources</span></span>|<span data-ttu-id="6f1e1-230">不支援</span><span class="sxs-lookup"><span data-stu-id="6f1e1-230">Not supported</span></span>|  
  
## <a name="performing-specific-resgenexe-tasks"></a><span data-ttu-id="6f1e1-231">執行特定 Resgen.exe 工作</span><span class="sxs-lookup"><span data-stu-id="6f1e1-231">Performing Specific Resgen.exe Tasks</span></span>  
 <span data-ttu-id="6f1e1-232">您可以透過不同方式來使用 Resgen.exe：將文字或 XML 架構資源檔編譯成二進位檔案、資源檔格式間的轉換和產生包裝 <xref:System.Resources.ResourceManager> 功能並提供存取資源的類別。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-232">You can use Resgen.exe in diverse ways: to compile a text-based or XML-based resource file into a binary file, to convert between resource file formats, and to generate a class that wraps <xref:System.Resources.ResourceManager> functionality and provides access to resources.</span></span> <span data-ttu-id="6f1e1-233">本節提供各項工作的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-233">This section provides detailed information about each task:</span></span>  
  
- [<span data-ttu-id="6f1e1-234">將資源編譯成二進位檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-234">Compiling Resources into a Binary File</span></span>](resgen-exe-resource-file-generator.md#Compiling)  
  
- [<span data-ttu-id="6f1e1-235">資源檔類型間的轉換</span><span class="sxs-lookup"><span data-stu-id="6f1e1-235">Converting Between Resource File Types</span></span>](resgen-exe-resource-file-generator.md#Convert)  
  
- [<span data-ttu-id="6f1e1-236">編譯或轉換多個檔案</span><span class="sxs-lookup"><span data-stu-id="6f1e1-236">Compiling or Converting Multiple Files</span></span>](resgen-exe-resource-file-generator.md#Multiple)  
  
- [<span data-ttu-id="6f1e1-237">將資源匯出至 .resw 檔案</span><span class="sxs-lookup"><span data-stu-id="6f1e1-237">Exporting Resources to a .resw File</span></span>](resgen-exe-resource-file-generator.md#Exporting)  
  
- [<span data-ttu-id="6f1e1-238">條件式編譯資源</span><span class="sxs-lookup"><span data-stu-id="6f1e1-238">Conditionally Compiling Resources</span></span>](resgen-exe-resource-file-generator.md#Conditional)  
  
- [<span data-ttu-id="6f1e1-239">產生強型別資源類別</span><span class="sxs-lookup"><span data-stu-id="6f1e1-239">Generating a Strongly Typed Resource Class</span></span>](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>
### <a name="compiling-resources-into-a-binary-file"></a><span data-ttu-id="6f1e1-240">將資源編譯成二進位檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-240">Compiling Resources into a Binary File</span></span>  
 <span data-ttu-id="6f1e1-241">最常見的 Resgen.exe 是用來將文字架構的資源檔 (.txt 或 .restext 檔) 或 XML 架構資源檔 (.resx 檔) 編譯成二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-241">The most common use of Resgen.exe is to compile a text-based resource file (a .txt or .restext file) or an XML-based resource file (a .resx file) into a binary .resources file.</span></span> <span data-ttu-id="6f1e1-242">輸出檔可以由語言編譯器內嵌在主要組件或由[組件連結器 (AL.exe)](al-exe-assembly-linker.md) 內嵌在附屬組件。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-242">The output file then can be embedded in a main assembly by a language compiler or in a satellite assembly by [Assembly Linker (AL.exe)](al-exe-assembly-linker.md).</span></span>  
  
 <span data-ttu-id="6f1e1-243">編譯資源檔的語法是：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-243">The syntax to compile a resource file is:</span></span>  
  
```console  
resgen inputFilename [outputFilename]
```  
  
 <span data-ttu-id="6f1e1-244">其中的參數：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-244">where the parameters are:</span></span>  
  
 `inputFilename`  
 <span data-ttu-id="6f1e1-245">要編譯的資源檔檔案名稱 (包括副檔名)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-245">The file name, including the extension, of the resource file to compile.</span></span> <span data-ttu-id="6f1e1-246">Resgen.exe 只編譯使用 .txt、.restext 或 .resx 為副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-246">Resgen.exe only compiles files with extensions of .txt, .restext, or .resx.</span></span>  
  
 `outputFilename`  
 <span data-ttu-id="6f1e1-247">輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-247">The name of the output file.</span></span> <span data-ttu-id="6f1e1-248">如果您省略 `outputFilename`，Resgen.exe 會在和 `inputFilename` 相同的目錄下建立具有 `inputFilename` 之根檔案名稱的 .resources 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-248">If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`.</span></span> <span data-ttu-id="6f1e1-249">如果 `outputFilename` 包含一個目錄路徑，則目錄必須存在。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-249">If `outputFilename` includes a directory path, the directory must exist.</span></span>  
  
 <span data-ttu-id="6f1e1-250">您可以在 .resource 檔的檔案名稱中指定並將命名空間與根檔案名稱以一個句號分隔，為 .resources 檔案提供完整命名空間。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-250">You provide a fully qualified namespace for the .resources file by specifying it in the file name and separating it from the root file name by a period.</span></span> <span data-ttu-id="6f1e1-251">例如，如果 `outputFilename` 是 `MyCompany.Libraries.Strings.resources`，則命名空間是 MyCompany.Libraries。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-251">For example, if `outputFilename` is `MyCompany.Libraries.Strings.resources`, the namespace is MyCompany.Libraries.</span></span>  
  
 <span data-ttu-id="6f1e1-252">下列命令會讀取 Resources.txt 中的名稱/值組，並且寫入名為 Resources.resources 的二進位 .resources 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-252">The following command reads the name/value pairs in Resources.txt and writes a binary .resources file named Resources.resources.</span></span> <span data-ttu-id="6f1e1-253">由於並未明確指定輸出檔名，因此預設會接收與輸入檔相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-253">Because the output file name is not specified explicitly, it receives the same name as the input file by default.</span></span>  
  
```console  
resgen Resources.txt
```  
  
 <span data-ttu-id="6f1e1-254">下列命令會讀取 Resources.restext 中的名稱/值組，並且寫入名為 StringResources.resources 的二進位 .resources 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-254">The following command reads the name/value pairs in Resources.restext and writes a binary resources file named StringResources.resources.</span></span>  
  
```console  
resgen Resources.restext StringResources.resources  
```  
  
 <span data-ttu-id="6f1e1-255">下列命令會讀取 XML 架構檔案且名稱為 Resources.resx 的輸入檔，並寫入命名為 Resources.resources 的二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-255">The following command reads an XML-based input file named Resources.resx and writes a binary .resources file named Resources.resources.</span></span>  
  
```console  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>
### <a name="converting-between-resource-file-types"></a><span data-ttu-id="6f1e1-256">資源檔類型間的轉換</span><span class="sxs-lookup"><span data-stu-id="6f1e1-256">Converting Between Resource File Types</span></span>  
 <span data-ttu-id="6f1e1-257">除了將文字或 XML 架構的資源檔編譯成二進位 .resources 檔外，Resgen.exe 能將任何支援的檔案類型轉換為其他任何支援的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-257">In addition to compiling text-based or XML-based resource files into binary .resources files, Resgen.exe can convert any supported file type to any other supported file type.</span></span> <span data-ttu-id="6f1e1-258">這表示它可以執行下列轉換：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-258">This means that it can perform the following conversions:</span></span>  
  
- <span data-ttu-id="6f1e1-259">.txt 檔和 .restext 檔轉換為 .resx 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-259">.txt and .restext files to .resx files.</span></span>  
  
- <span data-ttu-id="6f1e1-260">.resx 檔轉換為 .txt 和 .restext 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-260">.resx files to .txt and .restext files.</span></span>  
  
- <span data-ttu-id="6f1e1-261">.resources 檔轉換為 .txt 檔和 .restext 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-261">.resources files to .txt and .restext files.</span></span>  
  
- <span data-ttu-id="6f1e1-262">.resources 檔轉換為 .resx 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-262">.resources files to .resx files.</span></span>  
  
 <span data-ttu-id="6f1e1-263">語法與上一節顯示的內容相同。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-263">The syntax is the same as that shown in the previous section.</span></span>  
  
 <span data-ttu-id="6f1e1-264">此外，您可以使用 Resgen.exe 將 .NET Framework 元件中的內嵌資源轉換為 .resw 檔案 tor Windows 8.x 存放區應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-264">In addition, you can use Resgen.exe to convert embedded resources in a .NET Framework assembly to a .resw file tor Windows 8.x Store apps.</span></span>  
  
 <span data-ttu-id="6f1e1-265">下列命令會讀取名為 Resources.resources 的二進位 .resources 檔案，並寫入名為 Resources.resx 的 XML 架構輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-265">The following command reads a binary resources file Resources.resources and writes an XML-based output file named Resources.resx.</span></span>  
  
```console  
resgen Resources.resources Resources.resx  
```  
  
 <span data-ttu-id="6f1e1-266">下列命令會讀取命名為 StringResources.txt 的文字架構資源檔，並寫入名為 LibraryResources.resx 的 XML 架構資源檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-266">The following command reads a text-based resources file named StringResources.txt and writes an XML-based resources file named LibraryResources.resx.</span></span> <span data-ttu-id="6f1e1-267">除了包含字串資源之外，.resx 檔也可以用來儲存非字串資源。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-267">In addition to containing string resources, the .resx file could also be used to store non-string resources.</span></span>  
  
```console  
resgen StringResources.txt LibraryResources.resx  
```  
  
 <span data-ttu-id="6f1e1-268">下列兩個命令會讀取名稱為 Resources.resx 的 XML 架構資源檔案，並寫入名為 Resources.txt 和 Resources.restext 的文字檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-268">The following two commands read an XML-based resources file named Resources.resx and write text files named Resources.txt and Resources.restext.</span></span> <span data-ttu-id="6f1e1-269">請注意，如果 .resx 檔內含任何嵌入的物件，就無法正確的轉換成文字檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-269">Note that if the .resx file contains any embedded objects, they will not be accurately converted into the text files.</span></span>  
  
```console  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>
### <a name="compiling-or-converting-multiple-files"></a><span data-ttu-id="6f1e1-270">編譯或轉換多個檔案</span><span class="sxs-lookup"><span data-stu-id="6f1e1-270">Compiling or Converting Multiple Files</span></span>  
 <span data-ttu-id="6f1e1-271">您可以使用 `/compile` 參數將一個資源檔清單透過單一作業轉換格式。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-271">You can use the `/compile` switch to convert a list of resource files from one format to another in a single operation.</span></span> <span data-ttu-id="6f1e1-272">語法為：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-272">The syntax is:</span></span>  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 <span data-ttu-id="6f1e1-273">下列命令會將三個檔案：StringResources.txt、TableResources.resw 和 ImageResources.resw，編譯成不同檔名的 .resources 檔案，分別為 StringResources.resources、TableResources.resources 和 ImageResources.resources。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-273">The following command compiles three files, StringResources.txt, TableResources.resw, and ImageResources.resw, into separate .resources files named StringResources.resources, TableResources.resources, and ImageResources.resources.</span></span>  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>
### <a name="exporting-resources-to-a-resw-file"></a><span data-ttu-id="6f1e1-274">將資源匯出至 .resw 檔案</span><span class="sxs-lookup"><span data-stu-id="6f1e1-274">Exporting Resources to a .resw File</span></span>  
 <span data-ttu-id="6f1e1-275">如果您正在開發 Windows 8.x 存放區應用程式，您可能會想要使用現有桌面應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-275">If you're developing a Windows 8.x Store app, you may want to use resources from an existing desktop app.</span></span> <span data-ttu-id="6f1e1-276">然而，這兩種應用程式支援不同的檔案格式。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-276">However, the two kinds of applications support different file formats.</span></span> <span data-ttu-id="6f1e1-277">在桌面應用程式中，文字檔 (.txt 或 .restext) 或 .resx 檔案的資源會編譯為二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-277">In desktop apps, resources in text (.txt or .restext) or .resx files are compiled into binary .resources files.</span></span> <span data-ttu-id="6f1e1-278">在 Windows 8.x 存放區應用程式中，.resw 檔案會編譯成二進位封裝資源索引（PRI）檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-278">In Windows 8.x Store apps, .resw files are compiled into binary package resource index (PRI) files.</span></span> <span data-ttu-id="6f1e1-279">您可以使用 Resgen.exe 將資源從可執行檔或附屬元件解壓縮，並將其寫入一個或多個可在開發 Windows 8.x 存放區應用程式時使用的 .resw 檔案，以填補此間隙。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-279">You can use Resgen.exe to bridge this gap by extracting resources from an executable or a satellite assembly and writing them to one or more .resw files that can be used when developing a Windows 8.x Store app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6f1e1-280">Visual Studio 會自動處理將便攜媒體櫃中的資源併入 Windows 8.x 存放區應用程式所需的所有轉換。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-280">Visual Studio automatically handles all conversions necessary for incorporating the resources in a portable library into a Windows 8.x Store app.</span></span> <span data-ttu-id="6f1e1-281">直接使用 Resgen.exe 將元件中的資源轉換為 .resw 檔案格式，僅適用于想要在 Visual Studio 以外開發 Windows 8.x 存放區應用程式的開發人員。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-281">Using Resgen.exe directly to convert the resources in an assembly to .resw file format is of interest only to developers who want to develop a Windows 8.x Store app outside of Visual Studio.</span></span>  
  
 <span data-ttu-id="6f1e1-282">從組件產生 .resw 檔案的語法是：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-282">The syntax to generate .resw files from an assembly is:</span></span>  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 <span data-ttu-id="6f1e1-283">其中的參數：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-283">where the parameters are:</span></span>  
  
 `filename.extension`  
 <span data-ttu-id="6f1e1-284">.NET Framework 組件的名稱 (可執行檔或 .dll)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-284">The name of a .NET Framework assembly (an executable or .DLL).</span></span> <span data-ttu-id="6f1e1-285">如果檔案不包含資源，Resgen.exe 不會建立任何檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-285">If the file contains no resources, Resgen.exe does not create any files.</span></span>  
  
 `outputDirectory`  
 <span data-ttu-id="6f1e1-286">.resw 檔案欲寫入的現有目錄。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-286">The existing directory to which to write the .resw files.</span></span> <span data-ttu-id="6f1e1-287">如果省略 `outputDirectory`，.resw 檔案會寫入目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-287">If `outputDirectory` is omitted, .resw files are written to the current directory.</span></span> <span data-ttu-id="6f1e1-288">Resgen.exe 會為每個在組件中的 .resources 檔案建立 .resw 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-288">Resgen.exe creates one .resw file for each .resources file in the assembly.</span></span> <span data-ttu-id="6f1e1-289">.resw 檔案的根檔案名稱與 .resources 檔的根名稱相同。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-289">The root file name of the .resw file is the same as the root name of the .resources file.</span></span>  
  
 <span data-ttu-id="6f1e1-290">下列命令會在 Win8Resources 目錄中為每個內嵌在 MyApp.exe 的 .resources 檔建立 .resw 檔案：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-290">The following command creates a .resw file in the Win8Resources directory for each .resources file embedded in MyApp.exe:</span></span>  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>
### <a name="conditionally-compiling-resources"></a><span data-ttu-id="6f1e1-291">條件式編譯資源</span><span class="sxs-lookup"><span data-stu-id="6f1e1-291">Conditionally Compiling Resources</span></span>  
 <span data-ttu-id="6f1e1-292">從 .NET Framework 4.5 開始，Resgen.exe 支援文字檔 (.txt 和 .restext) 中字串資源的條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-292">Starting with the .NET Framework 4.5, Resgen.exe supports conditional compilation of string resources in text (.txt and .restext) files.</span></span> <span data-ttu-id="6f1e1-293">這可讓您在多個組建組態中使用單一文字資源檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-293">This enables you to use a single text-based resource file in multiple build configurations.</span></span>  
  
 <span data-ttu-id="6f1e1-294">在 .txt 或 .restext 檔中，如果有定義符號，您可以使用 `#ifdef`…`#endif`</span><span class="sxs-lookup"><span data-stu-id="6f1e1-294">In a .txt or .restext file, you use the `#ifdef`…`#endif`</span></span> <span data-ttu-id="6f1e1-295">結構以包含二進位 .resources 檔的資源，如果未下義符號，則可以使用 `#if !`... `#endif` 結構以包含資源。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-295">construct to include a resource in the binary .resources file if a symbol is defined, and you use the `#if !`... `#endif` construct to include a resource if a symbol is not defined.</span></span> <span data-ttu-id="6f1e1-296">在編譯時期，您可以使用 `/define:` 選項緊接著符號的逗號分隔清單來定義符號。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-296">At compile time, you then define symbols by using the `/define:` option followed by a comma-delimited list of symbols.</span></span> <span data-ttu-id="6f1e1-297">這個對照會區分大小寫，`/define` 定義的符號大小寫必須與欲編譯的文字檔中的大小寫吻合。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-297">The comparison is cased-sensitive; the case of symbols defined by `/define` must match the case of symbols in the text files to be compiled.</span></span>  
  
 <span data-ttu-id="6f1e1-298">例如，下列名為 UIResources.rext 的檔案包含名為 `AppTitle` 的字串資源，根據是否定義符號，可以接受三個值之一：`PRODUCTION`、`CONSULT` 或 `RETAIL`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-298">For example, the following file named UIResources.rext includes a string resource named `AppTitle` that can take one of three values, depending on whether symbols named `PRODUCTION`, `CONSULT`, or `RETAIL` are defined.</span></span>  
  
```text
#ifdef PRODUCTION  
AppTitle=My Software Company Project Manager
#endif  
#ifdef CONSULT  
AppTitle=My Consulting Company Project Manager  
#endif  
#ifdef RETAIL  
AppTitle=My Retail Store Project Manager  
#endif  
FileMenuName=File  
```  
  
 <span data-ttu-id="6f1e1-299">檔案接下來可以藉由下列命令編譯成二進位的 .resources 檔案：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-299">The file can then be compiled into a binary .resources file with the following command:</span></span>  
  
```console  
resgen /define:CONSULT UIResources.restext  
```  
  
 <span data-ttu-id="6f1e1-300">這會導致該 .resources 檔案中包含兩個字串資源。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-300">This produces a .resources file that contains two string resources.</span></span> <span data-ttu-id="6f1e1-301">`AppTitle` 資源的值為 "My Consulting Company Project Manager"。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-301">The value of the `AppTitle` resource is "My Consulting Company Project Manager".</span></span>  
  
<a name="Strong"></a>
### <a name="generating-a-strongly-typed-resource-class"></a><span data-ttu-id="6f1e1-302">產生強類型資源類別</span><span class="sxs-lookup"><span data-stu-id="6f1e1-302">Generating a Strongly Typed Resource Class</span></span>  
 <span data-ttu-id="6f1e1-303">Resgen.exe 支援強類型資源 (會建立包含一組靜態唯讀屬性的類別，以封裝對資源的存取)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-303">Resgen.exe supports strongly typed resources, which encapsulates access to resources by creating classes that contain a set of static read-only properties.</span></span> <span data-ttu-id="6f1e1-304">這提供直接呼叫 <xref:System.Resources.ResourceManager> 類別的方法來擷取資源。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-304">This provides an alternative to calling the methods of the <xref:System.Resources.ResourceManager> class directly to retrieve resources.</span></span> <span data-ttu-id="6f1e1-305">您可以使用 Resgen.exe 中的 `/str` 選項來啟用強類型資源的支援，以包裝 <xref:System.Resources.Tools.StronglyTypedResourceBuilder> 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-305">You can enable strongly typed resource support by using the `/str` option in Resgen.exe, which wraps the functionality of the <xref:System.Resources.Tools.StronglyTypedResourceBuilder> class.</span></span> <span data-ttu-id="6f1e1-306">當您指定 `/str` 選項時，Resgen.exe 的輸出會是一個包含強類型屬性的類別 (這類屬性與輸入參數中所參考的資源相符)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-306">When you specify the `/str` option, the output of Resgen.exe is a class that contains strongly typed properties that match the resources that are referenced in the input parameter.</span></span> <span data-ttu-id="6f1e1-307">這個類別可對已處理檔案中可取得資源的強類型提供唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-307">This class provides strongly typed read-only access to the resources that are available in the file processed.</span></span>  
  
 <span data-ttu-id="6f1e1-308">建立強類型資源的語法是：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-308">The syntax to create a strongly typed resource is:</span></span>  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 <span data-ttu-id="6f1e1-309">參數為：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-309">The parameters and switches are:</span></span>  
  
 `inputFilename`  
 <span data-ttu-id="6f1e1-310">欲產生強類型資源類別的資源檔之檔案名稱 (包括副檔名)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-310">The file name, including the extension, of the resource file for which to generate a strongly typed resource class.</span></span> <span data-ttu-id="6f1e1-311">檔案可以是文字、XML 架構或二進位 .resources 檔，它可以使用 .txt、.restext、.resw 或 .resources 副檔名。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-311">The file can be a text-based, XML-based, or binary .resources file; it can have an extension of .txt, .restext, .resw, or .resources.</span></span>  
  
 `outputFilename`  
 <span data-ttu-id="6f1e1-312">輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-312">The name of the output file.</span></span> <span data-ttu-id="6f1e1-313">如果 `outputFilename` 包含一個目錄路徑，則目錄必須存在。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-313">If `outputFilename` includes a directory path, the directory must exist.</span></span> <span data-ttu-id="6f1e1-314">如果您省略 `outputFilename`，Resgen.exe 會在和 `inputFilename` 相同的目錄下建立具有 `inputFilename` 之根檔案名稱的 .resources 檔。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-314">If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`.</span></span>  
  
 <span data-ttu-id="6f1e1-315">`outputFilename` 可以是文字、XML 架構或二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-315">`outputFilename` can be a text-based, XML-based, or binary .resources file.</span></span> <span data-ttu-id="6f1e1-316">如果 `outputFilename` 的副檔名與 `inputFilename` 的副檔名不同，Resgen.exe 會執行檔案轉換。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-316">If the file extension of `outputFilename` is different from the file extension of `inputFilename`, Resgen.exe performs the file conversion.</span></span>  
  
 <span data-ttu-id="6f1e1-317">如果 `inputFilename` 為 .resources 檔案且 `outputFilename` 也是 .resources 檔，則 Resgen.exe 會複製 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-317">If `inputFilename` is a .resources file, Resgen.exe copies the .resources file if `outputFilename` is also a .resources file.</span></span> <span data-ttu-id="6f1e1-318">如果省略 `outputFilename`，Resgen.exe 會覆寫具有相同 .resources 檔案的 `inputFilename`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-318">If `outputFilename` is omitted, Resgen.exe overwrites `inputFilename` with an identical .resources file.</span></span>  
  
 <span data-ttu-id="6f1e1-319">*language*</span><span class="sxs-lookup"><span data-stu-id="6f1e1-319">*language*</span></span>  
 <span data-ttu-id="6f1e1-320">要在其中產生強型別資源類別之原始程式碼的語言。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-320">The language in which to generate source code for the strongly typed resource class.</span></span> <span data-ttu-id="6f1e1-321">針對 C# 程式碼，可能的值為 `cs`、`C#` 和 `csharp`；針對 Visual Basic 程式碼，為 `vb` 和 `visualbasic`；針對 VBScript 程式碼，為 `vbs` 和 `vbscript`；針對 C++ 程式碼，為 `c++`、`mc` 和 `cpp`。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-321">Possible values are `cs`, `C#`, and `csharp` for C# code, `vb` and `visualbasic` for Visual Basic code, `vbs` and `vbscript` for VBScript code, and `c++`, `mc`, and `cpp` for C++ code.</span></span>  
  
 <span data-ttu-id="6f1e1-322">*命名空間*</span><span class="sxs-lookup"><span data-stu-id="6f1e1-322">*namespace*</span></span>  
 <span data-ttu-id="6f1e1-323">包含強類型資源類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-323">The namespace that contains the strongly typed resource class.</span></span> <span data-ttu-id="6f1e1-324">.resources 檔案和資源類別應該有相同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-324">The .resources file and the resource class should have the same namespace.</span></span> <span data-ttu-id="6f1e1-325">如需指定 `outputFilename` 的命名空間之詳細資訊，請參閱[編譯資源至二進位檔中](resgen-exe-resource-file-generator.md#Compiling)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-325">For information about specifying the namespace in the `outputFilename`, see [Compiling Resources into a Binary File](resgen-exe-resource-file-generator.md#Compiling).</span></span> <span data-ttu-id="6f1e1-326">如果省略 *namespace*，則命名空間不會包含資源類別。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-326">If *namespace* is omitted, the resource class is not contained in a namespace.</span></span>  
  
 <span data-ttu-id="6f1e1-327">*名*</span><span class="sxs-lookup"><span data-stu-id="6f1e1-327">*classname*</span></span>  
 <span data-ttu-id="6f1e1-328">強類型資源類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-328">The name of the strongly typed resource class.</span></span> <span data-ttu-id="6f1e1-329">這應該會對應於 .resources 檔的根名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-329">This should correspond to the root name of the .resources file.</span></span> <span data-ttu-id="6f1e1-330">例如，如果 Resgen.exe 產生名為 MyCompany.Libraries.Strings.resources 的 .resources 檔案，強類型資源類別的名稱會為 Strings。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-330">For example, if Resgen.exe generates a .resources file named MyCompany.Libraries.Strings.resources, the name of the strongly typed resource class is Strings.</span></span> <span data-ttu-id="6f1e1-331">如果省略 *classname*，產生的類別會衍生自 `outputFilename` 的根目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-331">If *classname* is omitted, the generated class is derived from the root name of `outputFilename`.</span></span> <span data-ttu-id="6f1e1-332">如果省略 `outputFilename`，產生的類別會衍生自 `inputFilename` 的根目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-332">If `outputFilename` is omitted, the generated class is derived from the root name of `inputFilename`.</span></span>  
  
 <span data-ttu-id="6f1e1-333">*classname* 無法包含無效的字元 (如空白字元)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-333">*classname* cannot contain invalid characters such as embedded spaces.</span></span> <span data-ttu-id="6f1e1-334">如果 *classname* 包含空白字元，或如果 *classname* 預設是由 *inputFilename* 產生，且 *inputFilename* 包含空白字元，則 Resgen.exe 會以底線 (\_) 取代所有無效的字元。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-334">If *classname* contains embedded spaces, or if *classname* is generated by default from *inputFilename*, and *inputFilename* contains embedded spaces, Resgen.exe replaces all invalid characters with an underscore (\_).</span></span>  
  
 <span data-ttu-id="6f1e1-335">*filename*</span><span class="sxs-lookup"><span data-stu-id="6f1e1-335">*filename*</span></span>  
 <span data-ttu-id="6f1e1-336">類別檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-336">The name of the class file.</span></span>  
  
 `/publicclass`  
 <span data-ttu-id="6f1e1-337">讓強類型資源類別為公用類別而不是 `internal` (C#) 或 `Friend` (Visual Basic)。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-337">Makes the strongly typed resource class public rather than `internal` (in C#) or `Friend` (in Visual Basic).</span></span> <span data-ttu-id="6f1e1-338">這可讓資源從它們的內嵌組件外部存取。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-338">This allows the resources to be accessed from outside the assembly in which they are embedded.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6f1e1-339">當您建立強類型資源類別時，您的 .resources 檔案的名稱必須符合所產生程式碼的命名空間和類別名稱。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-339">When you create a strongly typed resource class, the name of your .resources file must match the namespace and class name of the generated code.</span></span> <span data-ttu-id="6f1e1-340">不過，Resgen.exe 可讓您指定所產生 .resources 檔案有不相容名稱的選項。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-340">However, Resgen.exe allows you to specify options that produce a .resources file that has an incompatible name.</span></span> <span data-ttu-id="6f1e1-341">為了解決這個行為，可在它產生之後重新命名輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-341">To work around this behavior, rename the output file after it has been generated.</span></span>  
  
 <span data-ttu-id="6f1e1-342">強類型資源類別具有下列成員：</span><span class="sxs-lookup"><span data-stu-id="6f1e1-342">The strongly typed resource class has the following members:</span></span>  
  
- <span data-ttu-id="6f1e1-343">無參數的函式，可以用來具現化強型別資源類別。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-343">A parameterless constructor, which can be used to instantiate the strongly typed resource class.</span></span>  
  
- <span data-ttu-id="6f1e1-344">`static` (C#) 或 `Shared` (Visual Basic) 和唯讀 `ResourceManager` 屬性，可傳回 <xref:System.Resources.ResourceManager> 管理強類型資源的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-344">A `static` (C#) or `Shared` (Visual Basic) and read-only `ResourceManager` property, which returns the <xref:System.Resources.ResourceManager> instance that manages the strongly typed resource.</span></span>  
  
- <span data-ttu-id="6f1e1-345">靜態 `Culture` 屬性，可讓您將文化特性設定為資源擷取使用。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-345">A static `Culture` property, which allows you to set the culture used for resource retrieval.</span></span> <span data-ttu-id="6f1e1-346">根據預設，它的值是為 `null`，表示已使用目前的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-346">By default, its value is `null`, which means that the current UI culture is used.</span></span>  
  
- <span data-ttu-id="6f1e1-347">在 .resource 檔中每個 resource 的 `static` (C#) 或 `Shared` (Visual Basic) 和唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-347">One `static` (C#) or `Shared` (Visual Basic) and read-only property for each resource in the .resources file.</span></span> <span data-ttu-id="6f1e1-348">屬性名稱是資源的名稱。-</span><span class="sxs-lookup"><span data-stu-id="6f1e1-348">The name of the property is the name of the resource.-</span></span>  
  
 <span data-ttu-id="6f1e1-349">例如，下列命令會將名為 StringResources.txt 編譯為 StringResources.resources，並且在一個名為 StringResources.vb 的 Visual Basic 原始程式碼中產生名為 `StringResources` 的類別，可用於存取資源管理員。</span><span class="sxs-lookup"><span data-stu-id="6f1e1-349">For example, the following command compiles a resource file named StringResources.txt into StringResources.resources and generates a class named `StringResources` in a Visual Basic source code file named StringResources.vb that can be used to access the Resource Manager.</span></span>  
  
```console  
resgen StringResources.txt /str:vb,,StringResources
```  
  
## <a name="see-also"></a><span data-ttu-id="6f1e1-350">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f1e1-350">See also</span></span>

- [<span data-ttu-id="6f1e1-351">工具</span><span class="sxs-lookup"><span data-stu-id="6f1e1-351">Tools</span></span>](index.md)
- [<span data-ttu-id="6f1e1-352">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="6f1e1-352">Resources in Desktop Apps</span></span>](../resources/index.md)
- [<span data-ttu-id="6f1e1-353">建立資源檔</span><span class="sxs-lookup"><span data-stu-id="6f1e1-353">Creating Resource Files</span></span>](../resources/creating-resource-files-for-desktop-apps.md)
- [<span data-ttu-id="6f1e1-354">Al.exe （元件連結器）</span><span class="sxs-lookup"><span data-stu-id="6f1e1-354">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="6f1e1-355">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="6f1e1-355">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
