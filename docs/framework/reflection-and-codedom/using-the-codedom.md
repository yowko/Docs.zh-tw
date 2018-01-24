---
title: "使用 CodeDOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cd2b8e8ecb0e5d451ebf3c6823144e4a90e0d79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="using-the-codedom"></a>使用 CodeDOM
CodeDOM 提供的類型代表許多常見的原始程式碼項目類型。 您可以設計程式，建置使用 CodeDOM 項目的原始程式碼模型，組合物件圖形。 此物件圖形可以轉譯成使用 CodeDOM 程式碼產生器的原始程式碼，處理受支援的程式設計語言。 您也可以使用 CodeDOM 將原始程式碼編譯成二進位組件。  
  
 常見的 CodeDOM 用法包括：  
  
-   產生樣板化程式碼：為 ASP.NET、XML Web 服務用戶端 proxy、程式碼精靈、設計工具，或其他程式碼發出機制產生程式碼。  
  
-   動態編譯：支援以單一或多種語言編譯程式碼。  
  
## <a name="building-a-codedom-graph"></a>建置 CodeDOM 圖形  
 <xref:System.CodeDom> 命名空間提供代表原始程式碼邏輯結構的類別，不受語言語法影響。  
  
### <a name="the-structure-of-a-codedom-graph"></a>CodeDOM 圖形的結構  
 CodeDOM 圖形的結構就像容器的樹狀結構。 每個可編譯 CodeDOM 圖形的最上層 (或根) 容器都是 <xref:System.CodeDom.CodeCompileUnit>。 原始程式碼模型的每個項目都必須透過圖形中 <xref:System.CodeDom.CodeObject> 屬性連結到圖形。  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>建置範例 Hello World 程式的原始程式碼模型  
 下列逐步解說提供如何建置 CodeDOM 物件圖形的範例，此物件圖形代表簡單的 Hello World 應用程式程式碼。 如需此程式碼範例的完整原始程式碼，請參閱 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 主題。  
  
#### <a name="creating-a-compile-unit"></a>建立編譯單位  
 CodeDOM 會定義名為 <xref:System.CodeDom.CodeCompileUnit> 的物件，如此可參考 CodeDOM 物件圖形，建立要編譯的原始程式碼模型。 **CodeCompileUnit** 的屬性可以儲存屬性、命名空間和組件的參考。  
  
 衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別的 CodeDom 提供者有方法可處理 **CodeCompileUnit** 所參考的物件圖形。  
  
 若要建立簡單應用程式的物件圖形，您必須組合原始程式碼模型，並從 **CodeCompileUnit** 參考它。  
  
 您可以使用本例示範的語法，建立新的編譯單位：  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <xref:System.CodeDom.CodeSnippetCompileUnit> 可以包含已使用目標語言的原始程式碼區段，但無法轉譯成其他語言。  
  
#### <a name="defining-a-namespace"></a>定義命名空間  
 若要定義命名空間，請使用適當的建構函式，或設定其 **Name** 屬性，建立 <xref:System.CodeDom.CodeNamespace> 並指派其名稱。  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>匯入命名空間  
 若要將命名空間匯入指示詞新增至命名空間，請新增 <xref:System.CodeDom.CodeNamespaceImport>，指示命名空間要匯入 **CodeNamespace.Imports** 集合。  
  
 下列程式碼會將匯入的 **System** 命名空間新增至名為 `samples` 的 **CodeNamespace** 的 **Imports** 集合：  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>將程式碼項目連結到物件圖形  
 形成 CodeDOM 圖形的所有程式碼項目都必須連結到 <xref:System.CodeDom.CodeCompileUnit>，亦即樹狀結構的根項目，此樹狀結構是圖形根物件屬性直接參考項目間的一系列參考。 設定容器物件屬性的物件，從容器物件建立參考。  
  
 下列陳述式會將 `samples` **CodeNamespace** 新增至根 **CodeCompileUnit** 的 **Namespaces** 集合屬性。  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>定義類型  
 若要宣告使用 CodeDOM 的類別、結構、介面或列舉，請建立新的 <xref:System.CodeDom.CodeTypeDeclaration>，並為它指派名稱。 下列範例會使用建構函式多載設定 **Name** 屬性，來示範此作業：  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 若要將類型新增到命名空間，請新增代表類型的 <xref:System.CodeDom.CodeTypeDeclaration>，新增至 **CodeNamespace** 的 **Types** 集合的命名空間。  
  
 下列範例示範如何將名為 `class1` 的類別新增至名為 `samples` 的 **CodeNamespace**：  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>將類別成員新增至類別  
 <xref:System.CodeDom> 命名空間提供各種不同的項目，可以用來代表類別成員。 每個類別成員皆可新增至 <xref:System.CodeDom.CodeTypeDeclaration> 的 **Members** 集合。  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>定義可執行檔的程式碼進入點方法  
 如果您要為可執行程式建置程式碼，就必須建立 <xref:System.CodeDom.CodeEntryPointMethod> 代表程式應該開始執行的那個方法，指示程式的進入點。  
  
 下例示範如何定義包含 <xref:System.CodeDom.CodeMethodInvokeExpression> 的進入點方法，呼叫 **System.Console.WriteLine** 列印 "Hello World!"：  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 下列陳述式會將名為 `Start` 的進入點方法新增至 `class1` 的 **Members** 集合：  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 現在名為 `compileUnit` 的 <xref:System.CodeDom.CodeCompileUnit> 包含簡單 Hello World 程式的 CodeDOM 圖形。 如需從 CodeDOM 圖形產生及編譯程式碼的相關資訊，請參閱[從 CodeDOM 圖形產生原始程式碼和編譯程式](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)。  
  
### <a name="more-information-on-building-a-codedom-graph"></a>建置 CodeDOM 圖形的詳細資訊  
 CodeDOM 支援許多程式設計語言中常見的程式碼項目類型，這些程式設計語言都支援 Common Language Runtime。 CodeDOM 的設計目的不是提供代表所有可能程式設計語言功能的項目。 無法簡單以 CodeDOM 項目表示的程式碼，可以封裝在 <xref:System.CodeDom.CodeSnippetExpression>、<xref:System.CodeDom.CodeSnippetStatement>、<xref:System.CodeDom.CodeSnippetTypeMember> 或 <xref:System.CodeDom.CodeSnippetCompileUnit> 中。 不過，CodeDOM 無法自動將程式碼片段轉譯成其他語言。  
  
 如需 CodeDOM 各類型的文件，請參閱 <xref:System.CodeDom> 命名空間的參考文件。  
  
 如需快速圖表，找出表示特定程式碼項目類型的 CodeDOM 項目，請參閱 [CodeDOM 快速參考](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)。
