---
title: XSLT 編譯器 (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 470dd0eb37d8081d388ef69b204293f568096a5e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45615040"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="b5a8b-102">XSLT 編譯器 (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="b5a8b-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="b5a8b-103">XSLT 編譯器 (xsltc.exe) 會編譯 XSLT 樣式表並產生組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="b5a8b-104">然後編譯的樣式表可以直接傳遞到新的 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 方法中。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b5a8b-105">您無法使用 xsltc.exe 產生簽署的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="b5a8b-106">xsltc.exe 工具隨附於 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="b5a8b-107">如需詳細資訊，請參閱 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a8b-108">語法</span><span class="sxs-lookup"><span data-stu-id="b5a8b-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="b5a8b-109">引數</span><span class="sxs-lookup"><span data-stu-id="b5a8b-109">Argument</span></span>  
  
|<span data-ttu-id="b5a8b-110">引數</span><span class="sxs-lookup"><span data-stu-id="b5a8b-110">Argument</span></span>|<span data-ttu-id="b5a8b-111">描述</span><span class="sxs-lookup"><span data-stu-id="b5a8b-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="b5a8b-112">指定樣式表的名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="b5a8b-113">樣式表必須是本機檔案或位於內部網路上。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="b5a8b-114">選項</span><span class="sxs-lookup"><span data-stu-id="b5a8b-114">Options</span></span>  
  
|<span data-ttu-id="b5a8b-115">選項</span><span class="sxs-lookup"><span data-stu-id="b5a8b-115">Option</span></span>|<span data-ttu-id="b5a8b-116">描述</span><span class="sxs-lookup"><span data-stu-id="b5a8b-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b5a8b-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="b5a8b-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="b5a8b-118">為下列樣式表的類別指定名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="b5a8b-119">類別名稱可以是完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="b5a8b-120">類別名稱預設為樣式表的名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="b5a8b-121">例如，如果編譯了樣式表 customers.xsl，預設類別名稱就是 customers。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="b5a8b-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="b5a8b-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="b5a8b-123">指定是否要產生偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="b5a8b-124">指定 `+` 或 `/debug` 會讓編譯器產生偵錯資訊，並將其放在程式資料庫 (PDB) 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="b5a8b-125">產生的 PDB 檔案名稱是 `assemblyName`.pdb。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="b5a8b-126">指定 `-` (當您未指定 `/debug` 時，它就會生效) 不會建立任何偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="b5a8b-127">產生正式版本組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-127">A retail assembly is generated.</span></span> <span data-ttu-id="b5a8b-128">**注意：** 在偵錯模式下編譯對於 XSLT 效能會有顯著的影響。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="b5a8b-129">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="b5a8b-130">隱藏編譯器著作權訊息，使其無法顯示。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="b5a8b-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="b5a8b-131">`/platform:` `string`</span></span>|<span data-ttu-id="b5a8b-132">指定可執行組件的平台。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="b5a8b-133">以下將描述有效的平台值：</span><span class="sxs-lookup"><span data-stu-id="b5a8b-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="b5a8b-134">`x86` 會編譯將由 32 位元、x86 相容的 Common Language Runtime 所執行的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="b5a8b-135">`x64` 會在支援 AMD64 或 EM64T 指令集的電腦上編譯將由 64 位元 Common Language Runtime 所執行的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]<span data-ttu-id="b5a8b-136"> 會在具有 [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] 處理器的電腦上編譯將由 64 位元 Common Language Runtime 所執行的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-136"> compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="b5a8b-137">`anycpu` 會編譯要在任何平台上執行的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="b5a8b-138">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-138">This is the default.</span></span>|  
|<span data-ttu-id="b5a8b-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="b5a8b-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="b5a8b-140">指定當做輸出的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="b5a8b-141">組件名稱預設為主要樣式表的名稱，如果有多個樣式表存在，則預設為第一個樣式表名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="b5a8b-142">如果此樣式表包含指令碼，指令碼會儲存到個別組件中。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="b5a8b-143">指令碼組件名稱是從主要組件名稱產生而來。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="b5a8b-144">例如，如果您指定 CustOrders.dll 當做組件名稱，第一個指令碼組件會命名為 CustOrders_Script1.dll。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="b5a8b-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="b5a8b-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="b5a8b-146">指定樣式表中是否允許 `document()` 函式、XSLT 指令碼或文件類型定義 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="b5a8b-147">預設行為會停用 DTD、`document()` 函式和指令碼的支援。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="b5a8b-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="b5a8b-148">`@` `file`</span></span>|<span data-ttu-id="b5a8b-149">讓您指定包含編譯器選項的檔案。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="b5a8b-150">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5a8b-151">備註</span><span class="sxs-lookup"><span data-stu-id="b5a8b-151">Remarks</span></span>  
 <span data-ttu-id="b5a8b-152">XSLT 方案可由多個樣式表模組所組成。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="b5a8b-153">xsltc.exe 工具會從樣式表產生組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="b5a8b-154">然後此組件可以傳遞到 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 方法中。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b5a8b-155">如此將有助於在某些 XSLT 部署案例中減少效能成本。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5a8b-156">您也必須將編譯的組件當做參考併入應用程式中。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="b5a8b-157">xsltc.exe 工具不會驗證類別 (`/class:``name`) 或組件 (`/out:``assemblyName`) 名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="b5a8b-158">如果這些名稱無效，Common Language Runtime 會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b5a8b-159">範例</span><span class="sxs-lookup"><span data-stu-id="b5a8b-159">Examples</span></span>  
 <span data-ttu-id="b5a8b-160">下列命令會編譯樣式表，並建立名為 booksort.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="b5a8b-161">下列命令會編譯樣式表，並建立名稱分別為 booksort.dll 和 booksort.pdb 的組件和 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="b5a8b-162">下列命令會編譯包含 msxsl:script 項目的樣式表，並建立兩個名為 calc.dll 和 calc_Script1.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="b5a8b-163">下列命令會啟用 DTD 處理和指令碼支援，並建立兩個名為 myTest.dll 和 myTest_Script1.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="b5a8b-164">下列命令會編譯兩個樣式表模組，並建立名為 booksort.dll 的單一組件。</span><span class="sxs-lookup"><span data-stu-id="b5a8b-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5a8b-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5a8b-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [<span data-ttu-id="b5a8b-166">如何：使用組件執行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="b5a8b-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
- [<span data-ttu-id="b5a8b-167">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="b5a8b-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
