---
title: "使用 CodeDOM"
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
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cd594e9087a158ab8d5372ad72019cf3e04c38af
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 使用 CodeDOM
CodeDOM 提供表示多種原始程式碼項目一般型別的型別。  您可以設計一個程式來建置使用 CodeDOM 項目的原始程式碼模型，以組譯物件 Graph。  這個物件 Graph 可以使用受支援的程式語言的 CodeDOM 程式碼產生器，轉譯成原始程式碼。  CodeDOM 也可以用於將原始程式碼編譯為二進位組件。  
  
 CodeDOM 的一些一般運用包括：  
  
-   樣板化程式碼產生：為 ASP.NET、XML Web Service 用戶端 Proxy、程式碼精靈、設計工具或其他程式碼發出機制產生程式碼。  
  
-   動態編譯：支援使用單一或多種語言的程式碼編譯。  
  
## 建置 CodeDOM 物件 Graph  
 <xref:System.CodeDom> 命名空間提供了表示原始程式碼邏輯結構的類別，不限定語言語法。  
  
### CodeDOM 物件 Graph 的結構  
 CodeDOM 物件 Graph 的結構就像容器樹狀結構。  每個可編譯的 CodeDOM 物件 Graph 最上面的容器或根容器為 <xref:System.CodeDom.CodeCompileUnit>。  原始程式碼模型的每個項目都必須在 Graph 中，透過 <xref:System.CodeDom.CodeObject> 的屬性連結到 Graph。  
  
### 建置範例 Hello World 程式的原始程式碼模型  
 以下逐步解說提供的範例，示範如何建置表示簡單 Hello World 應用程式程式碼的 CodeDOM 物件 Graph。  如需這個程式碼範例的完整原始程式碼，請參閱 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName> 主題。  
  
#### 建立編譯單位  
 CodeDOM 會定義一個名為 <xref:System.CodeDom.CodeCompileUnit> 的物件，它可以參考做為要編譯之原始程式碼的模型之 CodeDOM 物件 Graph。  **CodeCompileUnit** 的屬性 \(Property\) 可以儲存對屬性 \(Attribute\)、命名空間和組件的參考。  
  
 衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別的 CodeDom 提供者包含了可處理 **CodeCompileUnit** 參考的物件圖形之方法。  
  
 若要建立簡單應用程式的物件 Graph，您必須組譯原始程式碼模型，並且從 **CodeCompileUnit** 參考它。  
  
 您可以使用這個範例中示範的語法建立新的編譯單元：  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <xref:System.CodeDom.CodeSnippetCompileUnit> 可以包含已經在目標語言中的原始程式碼區段，但是不能轉譯為其他語言。  
  
#### 定義命名空間  
 若要定義命名空間，請建立 <xref:System.CodeDom.CodeNamespace>，並使用適當的建構函式或設定它的 **Name** 屬性，為它指派一個名稱。  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### 匯入命名空間  
 若要將命名空間匯入指示詞加入到命名空間，請加入指示要將命名空間匯入 **CodeNamespace.Imports** 集合的 <xref:System.CodeDom.CodeNamespaceImport>。  
  
 下列程式碼將 **System** 命名空間的匯入加入到名為 `samples` 之 **CodeNamespace** 的 **Imports** 集合中：  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### 將程式碼項目連結到物件 Graph 中  
 所有組成 CodeDOM 物件 Graph 的程式碼項目，都必須由 Graph 根物件屬性所直接參考項目之間的一系列參考來連結到 <xref:System.CodeDom.CodeCompileUnit>，後者是樹狀結構的根項目。  將物件設定為容器物件的屬性，建立來自容器物件的參考。  
  
 下列陳述式會將 `samples` **CodeNamespace** 加入到根 **CodeCompileUnit** 的 **Namespaces** 集合屬性中。  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### 定義型別  
 若要使用 CodeDOM 宣告類別、結構、介面或列舉型別，請建立一個新的 <xref:System.CodeDom.CodeTypeDeclaration>，並為它指派一個名稱。  下列範例使用建構函式多載，設定 **Name** 屬性來示範這項工作：  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 若要將型別加入命名空間，請加入表示此型別的 <xref:System.CodeDom.CodeTypeDeclaration>，將命名空間加入到 **CodeNamespace** 的 **Types** 集合。  
  
 下列範例示範如何將名為 `class1` 的類別加入到名為 `samples` 的 **CodeNamespace**：  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### 將類別成員加入到類別  
 <xref:System.CodeDom> 命名空間提供多種可以用來表示類別成員的項目。  每個類別成員都可以加入到 <xref:System.CodeDom.CodeTypeDeclaration> 的 **Members** 集合中。  
  
#### 為可執行檔定義程式碼進入點方法  
 如果您正在建置可執行程式的程式碼，就需要指示程式的進入點，其方法是建立 <xref:System.CodeDom.CodeEntryPointMethod>，以表示程式執行應該開始的方法。  
  
 下列範例將示範如何定義進入點方法，它含有呼叫 **System.Console.WriteLine** 來顯示 "Hello World\!" 的 <xref:System.CodeDom.CodeMethodInvokeExpression>：  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 下列陳述式將名為 `Start` 的進入點方法加入到 `class1` 的 **Members** 集合中：  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 現在，名為 `compileUnit` 的 <xref:System.CodeDom.CodeCompileUnit> 包含了簡單 Hello World 程式的 CodeDOM 物件 Graph。  如需從 CodeDOM 圖形產生及編譯程式碼的詳細資訊，請參閱[從 CodeDOM 圖形產生原始程式碼及編譯程式](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)。  
  
### 建置 CodeDOM 物件 Graph 的詳細資訊  
 CodeDOM 支援很多可以在支援 Common Language Runtime 的程式語言中找到的程式碼項目一般型別。  CodeDOM 並非設計用來提供能表示所有可能之程式語言功能的項目。  不容易以 CodeDOM 項目表示的程式碼可以封裝在 <xref:System.CodeDom.CodeSnippetExpression>、<xref:System.CodeDom.CodeSnippetStatement>、<xref:System.CodeDom.CodeSnippetTypeMember> 或 <xref:System.CodeDom.CodeSnippetCompileUnit> 中。  然而，片段不能使用 CodeDOM 自動轉譯成其他語言。  
  
 如需每個 CodeDOM 型別的文件，請參閱 <xref:System.CodeDom> 命名空間的參考文件。  
  
 如需快速圖表，找出表示特定程式碼項目類型的 CodeDOM 項目，請參閱 [CodeDOM 快速參考](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)。

