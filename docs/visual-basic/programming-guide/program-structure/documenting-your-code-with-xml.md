---
title: 使用 XML 在程式碼中加入文件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 58c8716450fd8310b81050c86dc297c5b7527761
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524500"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="319e8-102">使用 XML 在程式碼中加入文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="319e8-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="319e8-103">在 Visual Basic 中，您可以使用 XML 記錄您的程式碼</span><span class="sxs-lookup"><span data-stu-id="319e8-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="319e8-104">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="319e8-104">XML Documentation Comments</span></span>

<span data-ttu-id="319e8-105">Visual Basic 提供簡單的方式來自動建立專案的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="319e8-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="319e8-106">您可以自動產生類型和成員的 XML 基本架構，然後提供摘要、每個參數的描述性檔，以及其他備註。</span><span class="sxs-lookup"><span data-stu-id="319e8-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="319e8-107">使用適當的設定時，XML 檔會自動發出至與您的專案同名的 XML 檔案和 .xml 副檔名。</span><span class="sxs-lookup"><span data-stu-id="319e8-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="319e8-108">如需詳細資訊，請參閱 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="319e8-108">For more information, see [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="319e8-109">您可以使用 xml 檔案，或以 XML 的方式操作。</span><span class="sxs-lookup"><span data-stu-id="319e8-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="319e8-110">這個檔案位於與專案的輸出 .exe 或 .dll 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="319e8-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="319e8-111">XML 檔的開頭為 `'''`。</span><span class="sxs-lookup"><span data-stu-id="319e8-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="319e8-112">這些註解在處理時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="319e8-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="319e8-113">文件必須是語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="319e8-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="319e8-114">如果 XML 的格式不正確，則會產生警告，而且檔檔案會包含批註，指出發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="319e8-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="319e8-115">開發人員可以自由建立自己的標記集合。</span><span class="sxs-lookup"><span data-stu-id="319e8-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="319e8-116">有一組建議的標記（請參閱本主題中的「相關章節」）。</span><span class="sxs-lookup"><span data-stu-id="319e8-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="319e8-117">其中一些建議的標記具有特殊意義：</span><span class="sxs-lookup"><span data-stu-id="319e8-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="319e8-118">\<param> 標記是用來描述參數。</span><span class="sxs-lookup"><span data-stu-id="319e8-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="319e8-119">如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。</span><span class="sxs-lookup"><span data-stu-id="319e8-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="319e8-120">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="319e8-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="319e8-121">`cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。</span><span class="sxs-lookup"><span data-stu-id="319e8-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="319e8-122">編譯器會驗證此程式碼項目存在。</span><span class="sxs-lookup"><span data-stu-id="319e8-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="319e8-123">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="319e8-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="319e8-124">在尋找 `cref` 屬性中所描述的類型時，編譯器也會遵循任何 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="319e8-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="319e8-125">Visual Studio 中的 IntelliSense 會使用 \<summary > 標記來顯示類型或成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="319e8-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="319e8-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="319e8-126">Related Sections</span></span>

<span data-ttu-id="319e8-127">如需有關建立含有檔批註之 XML 檔案的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="319e8-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="319e8-128">-doc</span><span class="sxs-lookup"><span data-stu-id="319e8-128">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="319e8-129">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="319e8-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="319e8-130">處理 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="319e8-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="319e8-131">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="319e8-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="319e8-132">Visual Studio 中的 XML 工具</span><span class="sxs-lookup"><span data-stu-id="319e8-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="319e8-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="319e8-133">See also</span></span>

- [<span data-ttu-id="319e8-134">使用 Visual Basic 開發應用程式</span><span class="sxs-lookup"><span data-stu-id="319e8-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="319e8-135">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="319e8-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
