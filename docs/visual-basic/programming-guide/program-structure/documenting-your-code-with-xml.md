---
title: 使用 XML 加入程式碼註解
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590925"
---
# <a name="document-your-code-with-xml-visual-basic"></a><span data-ttu-id="0a19e-102">使用 XML 記錄您的程式碼（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0a19e-102">Document your code with XML (Visual Basic)</span></span>

<span data-ttu-id="0a19e-103">在 Visual Basic 中，您可以使用 XML 來記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a19e-103">In Visual Basic, you can document your code using XML.</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="0a19e-104">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="0a19e-104">XML documentation comments</span></span>

<span data-ttu-id="0a19e-105">Visual Basic 提供簡單的方式來自動建立專案的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="0a19e-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="0a19e-106">您可以自動產生類型和成員的 XML 基本架構，然後提供摘要、每個參數的描述性檔，以及其他備註。</span><span class="sxs-lookup"><span data-stu-id="0a19e-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="0a19e-107">使用適當的設定時，XML 檔會自動發出至 XML 檔案，該檔案具有與您專案相同的根檔案名。</span><span class="sxs-lookup"><span data-stu-id="0a19e-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same root file name as your project.</span></span> <span data-ttu-id="0a19e-108">如需詳細資訊，請參閱[-doc](../../reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="0a19e-108">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="0a19e-109">您可以使用 xml 檔案，或以 XML 的方式操作。</span><span class="sxs-lookup"><span data-stu-id="0a19e-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="0a19e-110">這個檔案位於與專案的輸出 .exe 或 .dll 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0a19e-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="0a19e-111">XML 檔的開頭為 `'''` 。</span><span class="sxs-lookup"><span data-stu-id="0a19e-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="0a19e-112">這些註解在處理時有一些限制：</span><span class="sxs-lookup"><span data-stu-id="0a19e-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="0a19e-113">文件必須是語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="0a19e-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="0a19e-114">如果 XML 的格式不正確，則會產生警告，而且檔檔案會包含批註，指出發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a19e-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="0a19e-115">開發人員可以自由建立自己的標記集合。</span><span class="sxs-lookup"><span data-stu-id="0a19e-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="0a19e-116">有一組建議的標記（請參閱[XML 註解標記](../../language-reference/xmldoc/index.md)）。</span><span class="sxs-lookup"><span data-stu-id="0a19e-116">There is a recommended set of tags (see [XML Comment Tags](../../language-reference/xmldoc/index.md)).</span></span> <span data-ttu-id="0a19e-117">其中一些建議的標記具有特殊意義：</span><span class="sxs-lookup"><span data-stu-id="0a19e-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="0a19e-118">\<param>標記是用來描述參數。</span><span class="sxs-lookup"><span data-stu-id="0a19e-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="0a19e-119">如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。</span><span class="sxs-lookup"><span data-stu-id="0a19e-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="0a19e-120">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="0a19e-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="0a19e-121">`cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。</span><span class="sxs-lookup"><span data-stu-id="0a19e-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="0a19e-122">編譯器會驗證此程式碼項目存在。</span><span class="sxs-lookup"><span data-stu-id="0a19e-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="0a19e-123">如果驗證失敗，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="0a19e-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="0a19e-124">在 `Imports` 尋找屬性中所描述的類型時，編譯器也會遵循任何語句 `cref` 。</span><span class="sxs-lookup"><span data-stu-id="0a19e-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="0a19e-125">\<summary>Visual Studio 中的 IntelliSense 會使用此標記來顯示類型或成員的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="0a19e-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0a19e-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="0a19e-126">Related sections</span></span>

<span data-ttu-id="0a19e-127">如需有關建立含有檔批註之 XML 檔案的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0a19e-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="0a19e-128">-doc</span><span class="sxs-lookup"><span data-stu-id="0a19e-128">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="0a19e-129">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="0a19e-129">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="0a19e-130">處理 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="0a19e-130">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="0a19e-131">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="0a19e-131">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="0a19e-132">Visual Studio 中的 XML 工具</span><span class="sxs-lookup"><span data-stu-id="0a19e-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="0a19e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a19e-133">See also</span></span>

- [<span data-ttu-id="0a19e-134">使用 Visual Basic 開發應用程式</span><span class="sxs-lookup"><span data-stu-id="0a19e-134">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="0a19e-135">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0a19e-135">Visual Basic Programming Guide</span></span>](../index.md)
