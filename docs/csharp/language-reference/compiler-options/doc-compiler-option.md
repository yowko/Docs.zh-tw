---
description: -doc (C# 編譯器選項)
title: -doc (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: b1d7fbbe98aaad16454fdd71c161f2a17a2f4f2e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173252"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="097c6-103">-doc (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="097c6-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="097c6-104">**-doc** 選項可讓您在 XML 檔案中放入文件註解。</span><span class="sxs-lookup"><span data-stu-id="097c6-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="097c6-105">語法</span><span class="sxs-lookup"><span data-stu-id="097c6-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="097c6-106">引數</span><span class="sxs-lookup"><span data-stu-id="097c6-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="097c6-107">XML 的輸出檔，填入編譯原始程式碼檔案中的註解。</span><span class="sxs-lookup"><span data-stu-id="097c6-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="097c6-108">備註</span><span class="sxs-lookup"><span data-stu-id="097c6-108">Remarks</span></span>  

 <span data-ttu-id="097c6-109">在原始程式碼檔案中，位在下列內容前面的文件註解，可以處理並新增至 XML 檔案︰</span><span class="sxs-lookup"><span data-stu-id="097c6-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="097c6-110">這類使用者定義型別，如[類別](../keywords/class.md)、[委派](../builtin-types/reference-types.md#the-delegate-type)或[介面](../keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="097c6-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="097c6-111">這類成員如欄位、[事件](../keywords/event.md)、[屬性](../../programming-guide/classes-and-structs/using-properties.md)或方法。</span><span class="sxs-lookup"><span data-stu-id="097c6-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="097c6-112">包含主要的原始程式碼檔案會先輸出為 XML。</span><span class="sxs-lookup"><span data-stu-id="097c6-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="097c6-113">若要以產生的 .xml 檔案搭配 [IntelliSense](/visualstudio/ide/using-intellisense) 功能使用，.xml 檔案的檔案名稱要和您想支援的組件同名，然後確定 .xml 檔案和組件位於相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="097c6-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="097c6-114">如此，在 Visual Studio 專案中參考組件時，也會找到 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="097c6-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="097c6-115">如需詳細資訊，請參閱[提供程式碼註解](/visualstudio/ide/reference/generate-xml-documentation-comments)。</span><span class="sxs-lookup"><span data-stu-id="097c6-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="097c6-116">除非您使用[-target： module](./target-module-compiler-option.md)編譯，否則 `file` 將會包含 \<assembly> \</assembly> 標記，指定包含編譯輸出檔之組件資訊清單的檔案名。</span><span class="sxs-lookup"><span data-stu-id="097c6-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="097c6-117">-doc 選項適用於所有輸入檔案，或者，如果設定於 [專案設定]，則適用於專案中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="097c6-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="097c6-118">若要停用與特定檔案或程式碼區段文件註解相關的警告，請使用[#pragma 警告](../preprocessor-directives/preprocessor-pragma-warning.md)。</span><span class="sxs-lookup"><span data-stu-id="097c6-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="097c6-119">如需從程式碼中的註解產生文件的方式，請參閱[建議使用的文件註解標籤](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="097c6-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="097c6-120">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="097c6-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="097c6-121">開啟專案的 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="097c6-121">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="097c6-122">按一下 [建置]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="097c6-122">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="097c6-123">修改 **XML 文件檔案**屬性。</span><span class="sxs-lookup"><span data-stu-id="097c6-123">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="097c6-124">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>。</span><span class="sxs-lookup"><span data-stu-id="097c6-124">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097c6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="097c6-125">See also</span></span>

- [<span data-ttu-id="097c6-126">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="097c6-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="097c6-127">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="097c6-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
