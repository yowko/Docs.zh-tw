---
title: 作法：使用 CodeDOM 建立 XML 文件檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 283fc91762bc4065bd9bd09efaa2bc0061451ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962732"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="3aff0-102">作法：使用 CodeDOM 建立 XML 文件檔案</span><span class="sxs-lookup"><span data-stu-id="3aff0-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="3aff0-103">CodeDOM 可以用來建立會產生 XML 文件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3aff0-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="3aff0-104">此程序涉及建立包含 XML 文件註解的 CodeDOM 圖表、產生程式碼，以及編譯可建立 XML 文件輸出的以編譯器選項產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3aff0-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="3aff0-105">建立包含 XML 文件註解的 CodeDOM 圖表</span><span class="sxs-lookup"><span data-stu-id="3aff0-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1. <span data-ttu-id="3aff0-106">為範例應用程式建立包含 CodeDOM 圖形的 <xref:System.CodeDom.CodeCompileUnit>。</span><span class="sxs-lookup"><span data-stu-id="3aff0-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="3aff0-107">使用 `docComment` 參數設定為 `true` 的 <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> 建構函式來建立 XML 文件註解項目和文字。</span><span class="sxs-lookup"><span data-stu-id="3aff0-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="3aff0-108">從 CodeCompileUnit 產生程式碼</span><span class="sxs-lookup"><span data-stu-id="3aff0-108">To generate the code from the CodeCompileUnit</span></span>  
  
1. <span data-ttu-id="3aff0-109">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法來產生程式碼，並建立要編譯的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="3aff0-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="3aff0-110">若要編譯程式碼，並產生文件檔案</span><span class="sxs-lookup"><span data-stu-id="3aff0-110">To compile the code and generate the documentation file</span></span>  
  
1. <span data-ttu-id="3aff0-111">將 **/doc** 編譯器選項新增至 <xref:System.CodeDom.Compiler.CompilerParameters> 物件的 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 屬性，並在編譯程式碼時將物件傳送至 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法建立 XML 文件檔。</span><span class="sxs-lookup"><span data-stu-id="3aff0-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="3aff0-112">範例</span><span class="sxs-lookup"><span data-stu-id="3aff0-112">Example</span></span>  
 <span data-ttu-id="3aff0-113">下列程式碼範例會建立有文件註解的 CodeDOM 圖表、從圖表產生程式碼檔案，以及編譯檔案並建立相關聯的 XML 文件檔案。</span><span class="sxs-lookup"><span data-stu-id="3aff0-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="3aff0-114">程式碼範例會在 HelloWorldDoc.xml 檔案中建立下列 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="3aff0-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
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
        <seealso cref="M:Samples.Class1.Main" />   
      </summary>  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="3aff0-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3aff0-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="3aff0-116">此程式碼範例需要設定 `FullTrust` 權限，才能順利執行。</span><span class="sxs-lookup"><span data-stu-id="3aff0-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aff0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3aff0-117">See also</span></span>

- [<span data-ttu-id="3aff0-118">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="3aff0-118">Documenting Your Code with XML</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="3aff0-119">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="3aff0-119">XML Documentation Comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="3aff0-120">XML 文件</span><span class="sxs-lookup"><span data-stu-id="3aff0-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
