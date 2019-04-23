---
title: HOW TO：使用 CodeDOM 建立類別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d431fd472df329dd0a8421483eb36b573dce775
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333167"
---
# <a name="how-to-create-a-class-using-codedom"></a>HOW TO：使用 CodeDOM 建立類別
下列程序示範如何建立及編譯 CodeDOM 圖表，其可產生包含兩個欄位、三種屬性、一種方法、一個建構函式和一個進入點的類別。  
  
1. 建立主控台應用程式，使用 CodeDOM 程式碼產生類別的原始程式碼。  
  
     在此範例中，則產生的類別命名為 `Sample`，而產生的程式碼類別名為 `CodeDOMCreatedClass`，其位於 SampleCode 檔案中。  
  
2. 在產生的類別中，初始化 CodeDOM 圖表並使用 CodeDOM 方法來定義所產生類別的成員、建構函式及進入點 (`Main` 方法)。  
  
     在此範例中，產生的類別有兩個欄位、 三個屬性、 建構函式、 方法和 `Main` 方法。  
  
3. 在產生之類別中，建立特定語言的程式碼提供者並呼叫其 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 圖表產生程式碼的方法。  
  
4. 編譯並執行應用程式產生的程式碼。  
  
     在此範例中，產生的程式碼是在名為 SampleCode 的檔案中。 編譯並執行此程式碼，請參閱範例輸出。  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>若要建立會執行 CodeDOM 程式碼的應用程式  
  
-   建立主控台應用程式類別以包含 CodeDOM 程式碼。 定義在類別中用以參考組件 (<xref:System.CodeDom.CodeCompileUnit>) 和類別 (<xref:System.CodeDom.CodeTypeDeclaration>) 的全域欄位，指定產生的來源檔案名稱，並宣告 `Main` 方法。  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>初始化 CodeDOM 圖表  
  
-   在主控台應用程式類別的建構函式中，初始化組件和類別，並將適當的宣告新增至 CodeDOM 圖表。  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>將成員新增至 CodeDOM 圖表  
  
-   將 <xref:System.CodeDom.CodeMemberField> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將欄位新增至 CodeDOM 圖表。  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   將 <xref:System.CodeDom.CodeMemberProperty> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將屬性新增至 CodeDOM 圖表。  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   將 <xref:System.CodeDom.CodeMemberMethod> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將方法新增至 CodeDOM 圖表。  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   將 <xref:System.CodeDom.CodeConstructor> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，將以建構函式新增至 CodeDOM 圖表。  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   將 <xref:System.CodeDom.CodeEntryPointMethod> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將進入點新增至 CodeDOM 圖表。  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>從 CodeDOM 圖表產生程式碼  
  
-   呼叫 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法，從 CodeDOM 圖表產生原始程式碼。  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>建立圖形並產生程式碼  
  
1. 將前面步驟建立的方法新增至步驟 1 定義的 `Main` 方法。  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. 編譯並執行產生的類別。  
  
## <a name="example"></a>範例  
 下列程式碼範例會顯示前幾個步驟的程式碼。  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 前例編譯並執行後，即會產生下列原始程式碼。  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 編譯並執行後，產生的原始程式碼會產生下列輸出。  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   此程式碼範例需要設定 `FullTrust` 權限，才能順利執行。  
  
## <a name="see-also"></a>另請參閱

- [使用 CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [從 CodeDOM 圖表產生和編譯原始程式碼](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
