---
title: -doc
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7dc75a0600c9694c4a20f028c810c6aca54eeb6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="-doc"></a><span data-ttu-id="ee107-102">-doc</span><span class="sxs-lookup"><span data-stu-id="ee107-102">-doc</span></span>
<span data-ttu-id="ee107-103">將文件註解處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee107-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee107-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee107-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee107-105">引數</span><span class="sxs-lookup"><span data-stu-id="ee107-105">Arguments</span></span>  
  
|<span data-ttu-id="ee107-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ee107-106">Term</span></span>|<span data-ttu-id="ee107-107">定義</span><span class="sxs-lookup"><span data-stu-id="ee107-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="ee107-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ee107-108">`+` &#124; `-`</span></span>|<span data-ttu-id="ee107-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="ee107-109">Optional.</span></span> <span data-ttu-id="ee107-110">指定 +，或簡稱`-doc`，會導致編譯器產生文件資訊，並將它放在 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee107-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="ee107-111">指定`-`就相當於不指定`-doc`，導致建立沒有文件資訊。</span><span class="sxs-lookup"><span data-stu-id="ee107-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="ee107-112">如果使用 `-doc:`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="ee107-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="ee107-113">指定輸出 XML 檔案，它會填入從編譯的原始程式碼檔案的註解。</span><span class="sxs-lookup"><span data-stu-id="ee107-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="ee107-114">如果檔案名稱包含空格，括住的名稱加上引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="ee107-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee107-115">備註</span><span class="sxs-lookup"><span data-stu-id="ee107-115">Remarks</span></span>  
 <span data-ttu-id="ee107-116">`-doc`選項會控制是否編譯器會產生包含文件註解的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee107-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="ee107-117">如果您使用`-doc:file`語法，`file`參數會指定 XML 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee107-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="ee107-118">如果您使用`-doc`或`-doc+`，編譯器會從可執行檔或編譯器所建立的文件庫中取得的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ee107-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="ee107-119">如果您使用`-doc-`或不指定`-doc`選項，編譯器不會建立 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee107-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="ee107-120">在原始程式檔中，文件註解可以出現之前的定義如下：</span><span class="sxs-lookup"><span data-stu-id="ee107-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="ee107-121">使用者定義類型，例如[類別](../../../visual-basic/language-reference/statements/class-statement.md)或[介面](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ee107-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="ee107-122">成員，例如欄位、[事件](../../../visual-basic/language-reference/statements/event-statement.md)，[屬性](../../../visual-basic/language-reference/statements/property-statement.md)，[函式](../../../visual-basic/language-reference/statements/function-statement.md)，或[副程式](../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee107-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="ee107-123">若要使用產生的 XML 檔案與 Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense)功能，可讓您想要支援的組件相同的 XML 檔案的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ee107-123">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="ee107-124">請確定 XML 檔案與組件相同的目錄中，讓組件參考時 Visual Studio 專案中，以及找到的.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee107-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="ee107-125">XML 文件檔並不需要在單一專案或專案所參考的專案中的程式碼的 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="ee107-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="ee107-126">除非您使用編譯`/target:module`，XML 檔案包含標記`<assembly></assembly>`。</span><span class="sxs-lookup"><span data-stu-id="ee107-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="ee107-127">這些標記會指定包含編譯輸出檔的組件資訊清單之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee107-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="ee107-128">請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)的方式來產生文件從您的程式碼中的註解。</span><span class="sxs-lookup"><span data-stu-id="ee107-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="ee107-129">若要設定-Visual Studio 中的文件整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="ee107-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ee107-130">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="ee107-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ee107-131">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="ee107-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ee107-132">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ee107-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ee107-133">3.設定中的值**產生 XML 文件檔**方塊。</span><span class="sxs-lookup"><span data-stu-id="ee107-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee107-134">範例</span><span class="sxs-lookup"><span data-stu-id="ee107-134">Example</span></span>  
 <span data-ttu-id="ee107-135">請參閱[記載您的程式碼使用 XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)範例。</span><span class="sxs-lookup"><span data-stu-id="ee107-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee107-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee107-136">See Also</span></span>  
 [<span data-ttu-id="ee107-137">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ee107-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ee107-138">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="ee107-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
