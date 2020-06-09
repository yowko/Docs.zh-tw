---
title: 如何：使用 CodeDOM 建立 XML 文件檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: b9e11a51048733dbfc42ff9f575e18effc80db07
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596242"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>如何：使用 CodeDOM 建立 XML 檔檔案

CodeDOM 可以用來建立會產生 XML 文件的程式碼。 此程序涉及建立包含 XML 文件註解的 CodeDOM 圖表、產生程式碼，以及編譯可建立 XML 文件輸出的以編譯器選項產生的程式碼。  
  
## <a name="create-a-codedom-graph"></a>建立 CodeDOM 圖形
  
1. 為範例應用程式建立包含 CodeDOM 圖形的 <xref:System.CodeDom.CodeCompileUnit>。  
  
2. 使用 `docComment` 參數設定為 `true` 的 <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> 建構函式來建立 XML 文件註解項目和文字。  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a>從 CodeCompileUnit 產生程式碼
  
1. 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法來產生程式碼，並建立要編譯的來源檔案。  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a>編譯器代碼並產生檔檔
  
1. 將 **/doc** 編譯器選項新增至 <xref:System.CodeDom.Compiler.CompilerParameters> 物件的 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 屬性，並在編譯程式碼時將物件傳送至 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法建立 XML 文件檔。  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>範例

下列程式碼範例會建立有文件註解的 CodeDOM 圖表、從圖表產生程式碼檔案，以及編譯檔案並建立相關聯的 XML 文件檔案。  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 程式碼範例會在*HelloWorldDoc*檔案中建立下列 xml 檔。  
  
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
  
## <a name="compile-permissions"></a>編譯許可權
  
此程式碼範例需要設定 `FullTrust` 權限，才能順利執行。
  
## <a name="see-also"></a>請參閱

- [使用 XML 記錄您的程式碼（Visual Basic）](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML 文件註解](../../csharp/programming-guide/xmldoc/index.md)
- [XML 檔（c + +）](/cpp/ide/xml-documentation-visual-cpp)
