---
title: "從 CodeDOM 圖表產生和編譯原始程式碼 | Microsoft Docs"
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
  - "組件 [.NET Framework], CodeDOM"
  - "程式碼編譯器"
  - "程式碼文件物件模型, 產生原始程式碼"
  - "程式碼文件物件模型, 圖形"
  - "程式碼產生器"
  - "CodeDOM, 產生原始程式碼"
  - "CodeDOM, 圖形"
  - "編譯組件"
  - "編譯原始程式碼, 多個語言"
  - "動態編譯"
  - "動態表示原始程式碼"
  - "產生 CodeDOM 圖形"
  - "產生多個語言的原始程式碼"
  - "使用 CodeDOM 繪圖"
  - "由 CodeDOM 輸出原始程式碼"
  - "產生原始程式碼"
  - "原始程式碼, 產生"
  - "樣板化的程式碼產生"
  - "將一個語言轉譯成另一個語言"
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# 從 CodeDOM 圖表產生和編譯原始程式碼
<xref:System.CodeDom.Compiler> 命名空間提供的介面可從 CodeDOM 物件 Graph 產生原始程式碼，並管理支援編譯器的編譯工作。  程式碼提供者可以根據 CodeDOM 物件 Graph，在特定程式語言中產生原始程式碼。  衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別通常可以為提供者支援的語言，提供產生及編譯程式碼的方法。  
  
## 使用 CodeDOM 程式碼提供者產生原始程式碼  
 若要在特定語言中產生原始程式碼，您需要表示要產生之原始程式碼結構的 CodeDOM 物件 Graph。  
  
 下列範例會示範如何建立 <xref:Microsoft.CSharp.CSharpCodeProvider> 的執行個體：  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 用來產生程式碼的 Graph 通常包含在 <xref:System.CodeDom.CodeCompileUnit> 中。  若要替包含 CodeDOM 物件 Graph 的 **CodeCompileUnit** 產生程式碼，請呼叫程式碼提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法。  這個方法有一個 <xref:System.IO.TextWriter> 的參數，用來產生原始程式碼，因此有時需要先建立可以寫入的 **TextWriter**。  下列範例示範從 **CodeCompileUnit** 產生程式碼，並將產生的原始程式碼寫入名為 HelloWorld.cs 的檔案。  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## 使用 CodeDOM 程式碼提供者編譯組件  
 **叫用編譯**  
  
 若要使用 CodeDom 提供者編譯組件，您必須具有要編譯之原始程式碼的語言編譯器，或是可以藉此產生要編譯之原始程式碼的 CodeDOM 物件 Graph。  
  
 如果要從 CodeDOM 物件 Graph 編譯，請將包含 Graph 的 <xref:System.CodeDom.CodeCompileUnit> 傳遞給程式碼提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> 方法。  如果您的原始程式碼檔案使用編譯器了解的語言，請將包含原始程式碼的檔案名稱傳遞給 CodeDom 提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法。  您也可以將包含原始程式碼的字串 \(使用編譯器了解的語言\) 傳遞給 CodeDom 提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> 方法。  
  
 **設定編譯參數**  
  
 CodeDom 提供者的所有標準編譯叫用方法，都有型別為 <xref:System.CodeDom.Compiler.CompilerParameters> 的參數，表示要用於編譯的選項。  
  
 您可以在 **CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> 屬性中，指定輸出組件的檔案名稱。  否則將會使用預設的輸出檔案名稱。  
  
 依預設，新的 **CompilerParameters** 在初始化時，其 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> 屬性會設定為 **false**。  如果您正在編譯可執行程式，必須將 **GenerateExecutable** 屬性設定為 **true**。  **GenerateExecutable** 設定為 **false** 時，編譯器將會產生類別庫。  
  
 如果在 CodeDOM 物件 Graph 中編譯可執行檔，必須在 Graph 中定義 <xref:System.CodeDom.CodeEntryPointMethod>。  如果有多個程式碼進入點，可能需要先確定是由哪個類別定義要使用的進入點，然後將 **CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> 屬性設定為該類別名稱。  
  
 若要在產生的可執行檔中加入偵錯資訊，請將 <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> 屬性設定為 **true**。  
  
 如果專案參考任何組件，您必須將組件名稱指定為 <xref:System.Collections.Specialized.StringCollection> 中的項目，如同叫用編譯時使用的 **CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> 屬性。  
  
 將 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> 屬性設為 **true**，可以編譯寫入記憶體而不是磁碟的組件。  在記憶體中產生組件時，可取得由 <xref:System.CodeDom.Compiler.CompilerResults> 之 <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> 屬性所產生組件的參考。  如果是將組件寫入磁碟，您可以從 **CompilerResults** 的 <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> 屬性取得產生的組件所在路徑。  
  
 若要指定叫用編譯程序時要用的自定指令行引數字串，請在 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 屬性中設定字串。  
  
 如果叫用編譯器程序時需要 Win32 安全性權杖，請在 <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> 屬性中指定權杖。  
  
 若要將 Win32 資源檔連結到編譯的組件中，請在 <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> 屬性中指定 Win32 資源檔的名稱。  
  
 若要指定暫停編譯的警告層級，請將 <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> 屬性設為代表暫停編譯之警告層級的整數。  將 <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> 屬性設定為 **true**，也可以將編譯器設定為遭遇警告時即暫停編譯。  
  
 下列程式碼範例將示範如何使用衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別的 CodeDom 提供者來編譯原始程式檔。  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## 初期支援的語言  
 .NET Framework 提供下列語言的程式碼編譯器和程式碼產生器：C\#、Visual Basic、C\+\+ 和 JScript。  CodeDOM 支援可藉由實作語言專屬的程式碼產生器和程式碼編譯器擴充至其他語言。  
  
## 請參閱  
 <xref:System.CodeDom>   
 <xref:System.CodeDom.Compiler>   
 [動態原始程式碼的產生和編譯](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)   
 [CodeDOM Quick Reference](http://msdn.microsoft.com/zh-tw/c77b8bfd-0a32-4e36-b59a-4f687f32c524)