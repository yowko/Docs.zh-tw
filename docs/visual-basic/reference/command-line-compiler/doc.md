---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 8b80629ce9b2cd62f10d9a53279b83ba41bc4ece
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097705"
---
# <a name="-doc"></a><span data-ttu-id="386f7-102">-doc</span><span class="sxs-lookup"><span data-stu-id="386f7-102">-doc</span></span>

<span data-ttu-id="386f7-103">將文件註解處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="386f7-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="386f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="386f7-104">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="386f7-105">或</span><span class="sxs-lookup"><span data-stu-id="386f7-105">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="386f7-106">引數</span><span class="sxs-lookup"><span data-stu-id="386f7-106">Arguments</span></span>  
  
|<span data-ttu-id="386f7-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="386f7-107">Term</span></span>|<span data-ttu-id="386f7-108">定義</span><span class="sxs-lookup"><span data-stu-id="386f7-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="386f7-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="386f7-109">`+` &#124; `-`</span></span>|<span data-ttu-id="386f7-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="386f7-110">Optional.</span></span> <span data-ttu-id="386f7-111">指定 + 或只 `-doc` 會導致編譯器產生檔資訊，並將其放入 XML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="386f7-111">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="386f7-112">指定 `-` 相當於不指定，因此不 `-doc` 會建立任何檔資訊。</span><span class="sxs-lookup"><span data-stu-id="386f7-112">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="386f7-113">如果使用 `-doc:`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="386f7-113">Required if `-doc:` is used.</span></span> <span data-ttu-id="386f7-114">指定輸出 XML 檔案，該檔案會填入編譯之原始程式碼檔案中的批註。</span><span class="sxs-lookup"><span data-stu-id="386f7-114">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="386f7-115">如果檔案名包含空格，請在名稱前後加上引號 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="386f7-115">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="386f7-116">備註</span><span class="sxs-lookup"><span data-stu-id="386f7-116">Remarks</span></span>  

 <span data-ttu-id="386f7-117">`-doc`選項會控制編譯器是否產生包含檔批註的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="386f7-117">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="386f7-118">如果您使用 `-doc:file` 語法，參數會 `file` 指定 XML 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="386f7-118">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="386f7-119">如果您使用 `-doc` 或 `-doc+` ，則編譯器會從編譯器所建立的可執行檔或程式庫取得 XML 檔案名。</span><span class="sxs-lookup"><span data-stu-id="386f7-119">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="386f7-120">如果您使用 `-doc-` 或未指定 `-doc` 選項，則編譯器不會建立 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="386f7-120">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="386f7-121">在原始程式碼檔中，檔批註可以在下列定義之前：</span><span class="sxs-lookup"><span data-stu-id="386f7-121">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="386f7-122">使用者定義類型，例如 [類別](../../language-reference/statements/class-statement.md) 或 [介面](../../language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="386f7-122">User-defined types, such as a [class](../../language-reference/statements/class-statement.md) or [interface](../../language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="386f7-123">成員，例如 field、 [event](../../language-reference/statements/event-statement.md)、 [property](../../language-reference/statements/property-statement.md)、 [function](../../language-reference/statements/function-statement.md)或 [副程式](../../language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="386f7-123">Members, such as a field, [event](../../language-reference/statements/event-statement.md), [property](../../language-reference/statements/property-statement.md), [function](../../language-reference/statements/function-statement.md), or [subroutine](../../language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="386f7-124">若要使用產生的 XML 檔案搭配 Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) 功能，請讓 XML 檔案的檔案名與您想要支援的元件相同。</span><span class="sxs-lookup"><span data-stu-id="386f7-124">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="386f7-125">請確定 XML 檔案與元件位於相同的目錄中，如此一來，當 Visual Studio 專案中參考元件時，也會找到 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="386f7-125">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="386f7-126">IntelliSense 無法針對專案內的程式碼，或專案所參考專案內的程式碼，使用 XML 檔檔案。</span><span class="sxs-lookup"><span data-stu-id="386f7-126">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="386f7-127">除非您使用進行編譯，否則 XML 檔案會 `-target:module` 包含標記 `<assembly></assembly>` 。</span><span class="sxs-lookup"><span data-stu-id="386f7-127">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="386f7-128">這些標記會指定包含編譯輸出檔案之組件資訊清單的檔案名。</span><span class="sxs-lookup"><span data-stu-id="386f7-128">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="386f7-129">如需從程式碼中的批註產生檔的方法，請參閱 [XML 註解標記](../../language-reference/xmldoc/index.md) 。</span><span class="sxs-lookup"><span data-stu-id="386f7-129">See [XML Comment Tags](../../language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="386f7-130">若要在 Visual Studio 整合式開發環境中設定-doc</span><span class="sxs-lookup"><span data-stu-id="386f7-130">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="386f7-131">1. 在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="386f7-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="386f7-132">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="386f7-132">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="386f7-133">2. 按一下 [ **編譯** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="386f7-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="386f7-134">3. 在 [ **產生 XML 檔** 檔案] 方塊中設定值。</span><span class="sxs-lookup"><span data-stu-id="386f7-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="386f7-135">範例</span><span class="sxs-lookup"><span data-stu-id="386f7-135">Example</span></span>  

 <span data-ttu-id="386f7-136">如需範例，請參閱 [使用 XML 記載您的程式碼](../../programming-guide/program-structure/documenting-your-code-with-xml.md) 。</span><span class="sxs-lookup"><span data-stu-id="386f7-136">See [Documenting Your Code with XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="386f7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="386f7-137">See also</span></span>

- [<span data-ttu-id="386f7-138">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="386f7-138">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="386f7-139">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="386f7-139">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
