---
title: "使用 XML 在程式碼中加入文件 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb1f366002c4f0c675c591d83aab1b31ef8f602
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="8b316-102">使用 XML 在程式碼中加入文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b316-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="8b316-103">在[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，您可以將您的程式碼使用 XML 文件</span><span class="sxs-lookup"><span data-stu-id="8b316-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="8b316-104">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="8b316-104">XML Documentation Comments</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="8b316-105">提供簡單的方法來自動建立專案的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="8b316-105"> provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="8b316-106">您可以自動產生的 XML 基本架構型別和成員，然後再提供摘要、 描述性的文件每個參數，以及其他備註。</span><span class="sxs-lookup"><span data-stu-id="8b316-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="8b316-107">適當的安裝程式，XML 文件，就會自動發出到 XML 檔案具有相同名稱做為副檔名為.xml 和您的專案。</span><span class="sxs-lookup"><span data-stu-id="8b316-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="8b316-108">如需詳細資訊，請參閱 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="8b316-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="8b316-109">可以使用或操作為 XML 的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8b316-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="8b316-110">這個檔案位於相同的目錄與您的專案輸出.exe 或.dll 檔中。</span><span class="sxs-lookup"><span data-stu-id="8b316-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="8b316-111">XML 文件開頭`'''`。</span><span class="sxs-lookup"><span data-stu-id="8b316-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="8b316-112">這些註解在處理時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="8b316-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="8b316-113">文件必須是語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="8b316-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="8b316-114">如果 XML 的格式不正確，則會產生警告，而且文件檔案包含註解指出發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8b316-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="8b316-115">開發人員可以自由建立自己的標記集合。</span><span class="sxs-lookup"><span data-stu-id="8b316-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="8b316-116">沒有一組建議的標記 （請參閱本主題中的 < 相關章節 >）。</span><span class="sxs-lookup"><span data-stu-id="8b316-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="8b316-117">其中一些建議的標記具有特殊意義：</span><span class="sxs-lookup"><span data-stu-id="8b316-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="8b316-118">\<param> 標記是用來描述參數。</span><span class="sxs-lookup"><span data-stu-id="8b316-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="8b316-119">如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。</span><span class="sxs-lookup"><span data-stu-id="8b316-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="8b316-120">如果驗證失敗，則編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="8b316-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="8b316-121">`cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。</span><span class="sxs-lookup"><span data-stu-id="8b316-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="8b316-122">編譯器會驗證此程式碼項目存在。</span><span class="sxs-lookup"><span data-stu-id="8b316-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="8b316-123">如果驗證失敗，則編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="8b316-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="8b316-124">編譯器也會遵守任何`Imports`陳述式時搜尋類型中所述`cref`屬性。</span><span class="sxs-lookup"><span data-stu-id="8b316-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="8b316-125">\<摘要 > 標記中的 IntelliSense 即可使用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]以顯示類型或成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="8b316-125">The \<summary> tag is used by IntelliSense in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b316-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="8b316-126">Related Sections</span></span>  
 <span data-ttu-id="8b316-127">如需建立文件註解的 XML 檔案的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="8b316-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="8b316-128">/doc</span><span class="sxs-lookup"><span data-stu-id="8b316-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="8b316-129">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="8b316-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="8b316-130">處理 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="8b316-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="8b316-131">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="8b316-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="8b316-132">Visual Studio 中的 XML 工具</span><span class="sxs-lookup"><span data-stu-id="8b316-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="8b316-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b316-133">See Also</span></span>  
 [<span data-ttu-id="8b316-134">使用 Visual Basic 開發應用程式</span><span class="sxs-lookup"><span data-stu-id="8b316-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)  
 [<span data-ttu-id="8b316-135">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="8b316-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
