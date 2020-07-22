---
title: 如何：使用 CodeDOM 建立 XML 文件檔案
description: 在此詳細範例中，請參閱如何產生程式碼，以使用程式碼檔物件模型（CodeDOM）來建立 XML 檔檔案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: f905b996910c6cfbc62378cc4cd6bb8c0e0e6fd4
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865147"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="12017-103">如何：使用 CodeDOM 建立 XML 檔檔案</span><span class="sxs-lookup"><span data-stu-id="12017-103">How to: Create an XML documentation file using CodeDOM</span></span>

<span data-ttu-id="12017-104">CodeDOM 可以用來建立會產生 XML 文件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="12017-104">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="12017-105">此程序涉及建立包含 XML 文件註解的 CodeDOM 圖表、產生程式碼，以及編譯可建立 XML 文件輸出的以編譯器選項產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="12017-105">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
## <a name="create-a-codedom-graph"></a><span data-ttu-id="12017-106">建立 CodeDOM 圖形</span><span class="sxs-lookup"><span data-stu-id="12017-106">Create a CodeDOM graph</span></span>
  
1. <span data-ttu-id="12017-107">為範例應用程式建立包含 CodeDOM 圖形的 <xref:System.CodeDom.CodeCompileUnit>。</span><span class="sxs-lookup"><span data-stu-id="12017-107">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="12017-108">使用 `docComment` 參數設定為 `true` 的 <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> 建構函式來建立 XML 文件註解項目和文字。</span><span class="sxs-lookup"><span data-stu-id="12017-108">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="12017-109">從 CodeCompileUnit 產生程式碼</span><span class="sxs-lookup"><span data-stu-id="12017-109">Generate the code from the CodeCompileUnit</span></span>
  
1. <span data-ttu-id="12017-110">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法來產生程式碼，並建立要編譯的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="12017-110">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="12017-111">編譯器代碼並產生檔檔</span><span class="sxs-lookup"><span data-stu-id="12017-111">Compile the code and generate the documentation file</span></span>
  
1. <span data-ttu-id="12017-112">將 **/doc** 編譯器選項新增至 <xref:System.CodeDom.Compiler.CompilerParameters> 物件的 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 屬性，並在編譯程式碼時將物件傳送至 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法建立 XML 文件檔。</span><span class="sxs-lookup"><span data-stu-id="12017-112">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="12017-113">範例</span><span class="sxs-lookup"><span data-stu-id="12017-113">Example</span></span>

<span data-ttu-id="12017-114">下列程式碼範例會建立有文件註解的 CodeDOM 圖表、從圖表產生程式碼檔案，以及編譯檔案並建立相關聯的 XML 文件檔案。</span><span class="sxs-lookup"><span data-stu-id="12017-114">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="12017-115">此程式碼範例會在*HelloWorldDoc.xml*檔案中建立下列 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="12017-115">The code example creates the following XML documentation in the *HelloWorldDoc.xml* file.</span></span>  
  
```xml  
<?xml version="1.0" ?>
<doc>  
  <assembly>  
    <name>HelloWorld</name>
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.
      </summary>
      <seealso cref="M:Samples.Class1.Main" />
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.
        <para>Add a new paragraph to the description.</para>
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compile-permissions"></a><span data-ttu-id="12017-116">編譯許可權</span><span class="sxs-lookup"><span data-stu-id="12017-116">Compile permissions</span></span>
  
<span data-ttu-id="12017-117">此程式碼範例需要設定 `FullTrust` 權限，才能順利執行。</span><span class="sxs-lookup"><span data-stu-id="12017-117">This code example requires the `FullTrust` permission set to execute successfully.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="12017-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12017-118">See also</span></span>

- [<span data-ttu-id="12017-119">使用 XML 記錄您的程式碼（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="12017-119">Document your code with XML (Visual Basic)</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="12017-120">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="12017-120">XML documentation comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="12017-121">XML 檔（c + +）</span><span class="sxs-lookup"><span data-stu-id="12017-121">XML documentation (C++)</span></span>](/cpp/ide/xml-documentation-visual-cpp)
