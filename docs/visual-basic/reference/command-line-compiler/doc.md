---
title: /doc
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f9d4f584f217e6996a499614b97f184b28664f8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="doc"></a><span data-ttu-id="f391d-102">/doc</span><span class="sxs-lookup"><span data-stu-id="f391d-102">/doc</span></span>
<span data-ttu-id="f391d-103">將文件註解處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f391d-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f391d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f391d-104">Syntax</span></span>  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f391d-105">引數</span><span class="sxs-lookup"><span data-stu-id="f391d-105">Arguments</span></span>  
  
|<span data-ttu-id="f391d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f391d-106">Term</span></span>|<span data-ttu-id="f391d-107">定義</span><span class="sxs-lookup"><span data-stu-id="f391d-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f391d-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f391d-108">`+` &#124; `-`</span></span>|<span data-ttu-id="f391d-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f391d-109">Optional.</span></span> <span data-ttu-id="f391d-110">指定 +，或簡稱`/doc`，會導致編譯器產生文件資訊，並將它放在 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f391d-110">Specifying +, or just `/doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="f391d-111">指定`-`就相當於不指定`/doc`，導致建立沒有文件資訊。</span><span class="sxs-lookup"><span data-stu-id="f391d-111">Specifying `-` is the equivalent of not specifying `/doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="f391d-112">如果使用 `/doc:`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="f391d-112">Required if `/doc:` is used.</span></span> <span data-ttu-id="f391d-113">指定輸出 XML 檔案，它會填入從編譯的原始程式碼檔案的註解。</span><span class="sxs-lookup"><span data-stu-id="f391d-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="f391d-114">如果檔案名稱包含空格，括住的名稱加上引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="f391d-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f391d-115">備註</span><span class="sxs-lookup"><span data-stu-id="f391d-115">Remarks</span></span>  
 <span data-ttu-id="f391d-116">`/doc`選項會控制是否編譯器會產生包含文件註解的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f391d-116">The `/doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="f391d-117">如果您使用`/doc:``file`語法，`file`參數會指定 XML 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f391d-117">If you use the `/doc:``file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="f391d-118">如果您使用`/doc`或`/doc+`，編譯器會從可執行檔或編譯器所建立的文件庫中取得的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f391d-118">If you use `/doc` or `/doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="f391d-119">如果您使用`/doc-`或不指定`/doc`選項，編譯器不會建立 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f391d-119">If you use `/doc-` or do not specify the `/doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="f391d-120">在原始程式檔中，文件註解可以出現之前的定義如下：</span><span class="sxs-lookup"><span data-stu-id="f391d-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="f391d-121">使用者定義類型，例如[類別](../../../visual-basic/language-reference/statements/class-statement.md)或[介面](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f391d-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="f391d-122">成員，例如欄位、[事件](../../../visual-basic/language-reference/statements/event-statement.md)，[屬性](../../../visual-basic/language-reference/statements/property-statement.md)，[函式](../../../visual-basic/language-reference/statements/function-statement.md)，或[副程式](../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f391d-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="f391d-123">若要使用產生的 XML 檔案，與[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense)功能，可讓您想要支援的組件相同的 XML 檔案的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f391d-123">To use the generated XML file with the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="f391d-124">請確認 XML 檔案位於與組件相同的目錄，以便組件中的參考時[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]專案的.xml 檔案位於以及。</span><span class="sxs-lookup"><span data-stu-id="f391d-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] project, the .xml file is found as well.</span></span> <span data-ttu-id="f391d-125">XML 文件檔並不需要在單一專案或專案所參考的專案中的程式碼的 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="f391d-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="f391d-126">除非您使用編譯`/target:module`，XML 檔案包含標記`<assembly></assembly>`。</span><span class="sxs-lookup"><span data-stu-id="f391d-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="f391d-127">這些標記會指定包含編譯輸出檔的組件資訊清單之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f391d-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="f391d-128">請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)的方式來產生文件從您的程式碼中的註解。</span><span class="sxs-lookup"><span data-stu-id="f391d-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="f391d-129">在 Visual Studio 中設定 /doc 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="f391d-129">To set /doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f391d-130">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f391d-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f391d-131">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f391d-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f391d-132">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f391d-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f391d-133">3.設定中的值**產生 XML 文件檔**方塊。</span><span class="sxs-lookup"><span data-stu-id="f391d-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f391d-134">範例</span><span class="sxs-lookup"><span data-stu-id="f391d-134">Example</span></span>  
 <span data-ttu-id="f391d-135">請參閱[記載您的程式碼使用 XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)範例。</span><span class="sxs-lookup"><span data-stu-id="f391d-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f391d-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="f391d-136">See Also</span></span>  
 [<span data-ttu-id="f391d-137">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f391d-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f391d-138">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="f391d-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
