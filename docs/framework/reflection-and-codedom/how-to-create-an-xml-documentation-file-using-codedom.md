---
title: "如何：使用 CodeDOM 建立 XML 文件檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7d5569fd22cc8469052cc318fd50a5f8ef94c1a9
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：使用 CodeDOM 建立 XML 文件檔案
CodeDOM 可用於建立產生 XML 文件的程式碼，  此程序包括建立包含 XML 文件註解的 CodeDOM 圖形、產生程式碼，並以建立 XML 文件輸出的編譯器選項編譯產生的程式碼。  
  
### 若要建立包含 XML 文件註解的 CodeDOM 圖形  
  
1.  建立 <xref:System.CodeDom.CodeCompileUnit>，其中包含範例應用程式的 CodeDOM 圖形。  
  
2.  使用 `docComment` 參數設定為 `true` 的 <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> 建構函式 \(Constructor\) 可建立 XML 文件註解項目和文字。  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### 若要從 CodeCompileUnit 產生程式碼  
  
1.  使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法可產生程式碼，並建立要編譯的原始程式檔 \(Source File\)。  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### 若要編譯程式碼並產生文件檔  
  
1.  將 **\/doc** 編譯器選項加入 <xref:System.CodeDom.Compiler.CompilerParameters> 物件的 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 屬性中，並將此物件傳遞至 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法，以便在編譯程式碼時建立 XML 文件檔。  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## 範例  
 下列程式碼範例會建立具有文件註解的 CodeDOM 圖形、從此圖形產生程式碼檔，並編譯檔案及建立關聯的 XML 文件檔。  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 此程式碼範例會在 HelloWorldDoc.xml 檔案中建立下列 XML 文件。  
  
```  
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
  
## 編譯程式碼  
  
-   此程式碼範例需要有 `FullTrust` 權限集合，才能執行成功。  
  
## <a name="see-also"></a>另請參閱  
 [使用 XML 加入程式碼註解](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [XML 文件註解](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)   
 [XML 文件](/cpp/ide/xml-documentation-visual-cpp)

