---
title: "如何：使用 CodeDOM 建立類別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼文件物件模型, 建立類別"
  - "程式碼文件物件模型, 圖形"
  - "CodeDOM, 建立類別"
  - "CodeDOM, 圖形"
  - "使用 CodeDOM 繪圖"
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用 CodeDOM 建立類別
下列程序說明如何建立及編譯會產生一個類別的 CodeDOM 圖形，此類別包含兩個欄位、三個屬性、一個方法、一個建構函式 \(Constructor\) 和一個進入點 \(Entry Point\)。  
  
1.  建立將使用 CodeDOM 程式碼產生類別之原始程式碼的主控台應用程式 \(Console Application\)。  
  
     在此範例中，產生的類別名為 `Sample`，而且產生的程式碼是一個名為 `CodeDOMCreatedClass` 的類別，位於名為 SampleCode 的檔案中。  
  
2.  在產生的類別中，初始化 CodeDOM 圖形及使用 CodeDOM 方法來定義產生之類別的成員、建構函式和進入點 \(`Main` 方法\)。  
  
     在此範例中，產生的類別有兩個欄位、三個屬性、一個建構函式、一個方法和一個 `Main` 方法。  
  
3.  在產生的類別中，建立特定語言的程式碼提供者，並呼叫其 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法，從圖形產生程式碼。  
  
4.  編譯並執行應用程式來產生程式碼。  
  
     在此範例中，產生的程式碼位於名為 SampleCode 的檔案中。  請編譯並執行該程式碼，以查看範例輸出。  
  
### 若要建立將執行 CodeDOM 程式碼的應用程式。  
  
-   建立一個包含 CodeDOM 程式碼的主控台應用程式類別。  定義此類別中用於參考組件 \(<xref:System.CodeDom.CodeCompileUnit>\) 和類別 \(<xref:System.CodeDom.CodeTypeDeclaration>\) 的全域欄位、指定產生之原始程式檔 \(Source File\) 的名稱，並宣告 `Main` 方法。  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### 若要初始化 CodeDOM 圖形  
  
-   在主控台應用程式類別的建構函式中，初始化組件和類別，並對 CodeDOM 圖形加入適當的宣告。  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### 若要將成員加入至 CodeDOM 圖形中  
  
-   將 <xref:System.CodeDom.CodeMemberField> 物件加入至此類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性中，藉此將欄位加入至 CodeDOM 圖形中。  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   將 <xref:System.CodeDom.CodeMemberProperty> 物件加入至此類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性中，藉此將屬性加入至 CodeDOM 圖形中。  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   將 <xref:System.CodeDom.CodeMemberMethod> 物件加入至此類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性中，藉此將方法加入至 CodeDOM 圖形中。  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   將 <xref:System.CodeDom.CodeConstructor> 物件加入至此類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性中，藉此將建構函式加入至 CodeDOM 圖形中。  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   將 <xref:System.CodeDom.CodeEntryPointMethod> 物件加入至此類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性中，藉此將進入點加入至 CodeDOM 圖形中。  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### 若要從 CodeDOM 圖形產生程式碼  
  
-   藉由呼叫 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法來從 CodeDOM 圖形產生原始程式碼。  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### 若要建立圖形及產生程式碼  
  
1.  將先前步驟中建立的方法加入至第一個步驟所定義的 `Main` 方法。  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  編譯並執行產生的類別。  
  
## 範例  
 下列程式碼範例顯示從先前步驟產生的程式碼。  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 當編譯並執行先前的範例後，會產生下列原始程式碼。  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 產生的原始程式碼會在編譯及執行時，產生下列輸出。  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## 編譯程式碼  
  
-   此程式碼範例需要有 `FullTrust` 權限集合，才能執行成功。  
  
## 請參閱  
 [使用 CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)   
 [從 CodeDOM 圖表產生和編譯原始程式碼](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)