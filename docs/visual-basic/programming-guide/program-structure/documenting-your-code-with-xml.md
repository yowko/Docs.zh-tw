---
title: 使用 XML 在程式碼中加入文件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: b99c37f30d595e114bb4625a2881a9f0b463f5e6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405175"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="21a2e-102">使用 XML 在程式碼中加入文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21a2e-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="21a2e-103">在 Visual Basic 中，您可以記錄使用 XML 程式碼</span><span class="sxs-lookup"><span data-stu-id="21a2e-103">In Visual Basic, you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="21a2e-104">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="21a2e-104">XML Documentation Comments</span></span>  
 <span data-ttu-id="21a2e-105">Visual Basic 提供簡單的方法來自動建立專案的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="21a2e-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="21a2e-106">您可以自動產生的 XML 基本架構，為您的型別和成員，然後再提供摘要、 描述性的文件每個參數，以及其他備註。</span><span class="sxs-lookup"><span data-stu-id="21a2e-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="21a2e-107">使用適當的設定，XML 文件就會自動發出至具有相同的名稱，為您的專案，而且副檔名為.xml 的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="21a2e-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="21a2e-108">如需詳細資訊，請參閱 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="21a2e-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="21a2e-109">可以取用或以其他方式操作 xml 的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="21a2e-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="21a2e-110">這個檔案位於與您的專案輸出.exe 或.dll 檔相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="21a2e-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="21a2e-111">XML 文件開頭`'''`。</span><span class="sxs-lookup"><span data-stu-id="21a2e-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="21a2e-112">這些註解在處理時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="21a2e-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="21a2e-113">文件必須是語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="21a2e-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="21a2e-114">如果 XML 的格式不正確，則會產生警告，而且文件檔案包含註解指出發現錯誤。</span><span class="sxs-lookup"><span data-stu-id="21a2e-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="21a2e-115">開發人員可以自由建立自己的標記集合。</span><span class="sxs-lookup"><span data-stu-id="21a2e-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="21a2e-116">沒有一組建議的標記 （請參閱本主題中的 < 相關章節 >）。</span><span class="sxs-lookup"><span data-stu-id="21a2e-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="21a2e-117">其中一些建議的標記具有特殊意義：</span><span class="sxs-lookup"><span data-stu-id="21a2e-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="21a2e-118">\<param> 標記是用來描述參數。</span><span class="sxs-lookup"><span data-stu-id="21a2e-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="21a2e-119">如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。</span><span class="sxs-lookup"><span data-stu-id="21a2e-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="21a2e-120">如果驗證失敗，則編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="21a2e-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="21a2e-121">`cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。</span><span class="sxs-lookup"><span data-stu-id="21a2e-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="21a2e-122">編譯器會驗證此程式碼項目存在。</span><span class="sxs-lookup"><span data-stu-id="21a2e-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="21a2e-123">如果驗證失敗，則編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="21a2e-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="21a2e-124">編譯器也會遵守任何`Imports`陳述式時尋找的型別中所述`cref`屬性。</span><span class="sxs-lookup"><span data-stu-id="21a2e-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="21a2e-125">\<摘要 > 標籤用 Visual Studio 中的 IntelliSense 來顯示類型或成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="21a2e-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="21a2e-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="21a2e-126">Related Sections</span></span>  
 <span data-ttu-id="21a2e-127">如需建立 XML 檔案與文件註解的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="21a2e-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="21a2e-128">/doc</span><span class="sxs-lookup"><span data-stu-id="21a2e-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="21a2e-129">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="21a2e-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)  
  
-   [<span data-ttu-id="21a2e-130">處理 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="21a2e-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="21a2e-131">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="21a2e-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="21a2e-132">Visual Studio 中的 XML 工具</span><span class="sxs-lookup"><span data-stu-id="21a2e-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="21a2e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21a2e-133">See Also</span></span>  
 [<span data-ttu-id="21a2e-134">使用 Visual Basic 開發應用程式</span><span class="sxs-lookup"><span data-stu-id="21a2e-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)  
 [<span data-ttu-id="21a2e-135">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="21a2e-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
