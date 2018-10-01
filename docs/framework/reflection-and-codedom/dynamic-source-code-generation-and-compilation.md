---
title: 動態原始程式碼的產生和編譯
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90b4214e244bc1f9c5f8e71782e604bd6c7b619
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108477"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="2542a-102">動態原始程式碼的產生和編譯</span><span class="sxs-lookup"><span data-stu-id="2542a-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="2542a-103">.NET Framework 包含稱為程式碼文件物件模型 (CodeDOM) 的機制，它可讓發出原始程式碼的程式開發人員在執行階段，根據代表要呈現之程式碼的單一模型，產生多種程式語言的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="2542a-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="2542a-104">為了代表原始程式碼，CodeDOM 項目會彼此連結，形成稱為 CodeDOM 圖形的資料結構，它會建立一些原始程式碼結構的模型。</span><span class="sxs-lookup"><span data-stu-id="2542a-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="2542a-105">`System.CodeDom` 命名空間會定義類型，可代表獨立於特定程式設計語言的原始碼邏輯結構。</span><span class="sxs-lookup"><span data-stu-id="2542a-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="2542a-106">`System.CodeDom.Compiler` 命名空間會定義類型，以從 CodeDOM 圖表產生原始程式碼，以及管理使用支援語言的原始程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="2542a-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="2542a-107">編譯器廠商或開發人員可以擴充支援的語言集。</span><span class="sxs-lookup"><span data-stu-id="2542a-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="2542a-108">程式需要產生適用於多種語言的程式模型原始程式碼，或是不確定目標語言的原始程式碼時，很適合使用與語言無關的原始程式碼模型。</span><span class="sxs-lookup"><span data-stu-id="2542a-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="2542a-109">比方說，某些設計工具使用 CodeDOM 作為語言抽象介面，以正確的程式設計語言產生程式碼，如果該語言支援 CodeDOM 的話。</span><span class="sxs-lookup"><span data-stu-id="2542a-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="2542a-110">.NET Framework 包含 <xref:Microsoft.CSharp.CSharpCodeProvider>、<xref:Microsoft.JScript.JScriptCodeProvider> 和 <xref:Microsoft.VisualBasic.VBCodeProvider> 的程式碼產生器和程式碼編譯器。</span><span class="sxs-lookup"><span data-stu-id="2542a-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2542a-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="2542a-111">In This Section</span></span>  
 [<span data-ttu-id="2542a-112">使用 CodeDOM</span><span class="sxs-lookup"><span data-stu-id="2542a-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="2542a-113">說明常見的用法，並示範使用 CodeDOM 建置簡單的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="2542a-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="2542a-114">從 CodeDOM 圖表產生原始程式碼和編譯程式</span><span class="sxs-lookup"><span data-stu-id="2542a-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="2542a-115">描述如何產生原始程式碼，和使用外部編譯器以及 `System.CodeDom.Compiler` 命名空間中定義的類別編譯產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2542a-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="2542a-116">如何：使用 CodeDOM 建立 XML 文件檔案</span><span class="sxs-lookup"><span data-stu-id="2542a-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="2542a-117">描述如何使用 CodeDOM 產生程式碼和 XML 文件註解，並編譯產生的程式碼，以建立 XML 文件輸出。</span><span class="sxs-lookup"><span data-stu-id="2542a-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="2542a-118">如何：使用 CodeDOM 建立類別</span><span class="sxs-lookup"><span data-stu-id="2542a-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="2542a-119">描述如何使用 CodeDOM 產生包含欄位、屬性、方法、建構函式和進入點的類別。</span><span class="sxs-lookup"><span data-stu-id="2542a-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2542a-120">參考資料</span><span class="sxs-lookup"><span data-stu-id="2542a-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="2542a-121">定義元素，代表以 Common Language Runtime 為目標之程式設計語言中的程式碼元素。</span><span class="sxs-lookup"><span data-stu-id="2542a-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="2542a-122">定義介面以便在執行階段產生和編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="2542a-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2542a-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="2542a-123">Related Sections</span></span>  
 [<span data-ttu-id="2542a-124">CodeDOM 快速參考</span><span class="sxs-lookup"><span data-stu-id="2542a-124">CodeDOM Quick Reference</span></span>](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 <span data-ttu-id="2542a-125">提供快速方法，讓開發人員尋找代表原始程式碼元素的 CodeDOM 元素。</span><span class="sxs-lookup"><span data-stu-id="2542a-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
