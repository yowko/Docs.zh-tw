---
title: "從 CodeDOM 圖表產生和編譯原始程式碼"
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
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b99dacb5a30cd7b12a5a5dd96bf9fe25b32ab984
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>從 CodeDOM 圖表產生和編譯原始程式碼
<xref:System.CodeDom.Compiler> 命名空間提供的介面，可從 CodeDOM 物件圖形產生原始程式碼以及使用支援的編譯器管理編譯。 程式碼提供者可根據 CodeDOM 圖表以特定的程式設計語言產生原始程式碼。 衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別一般會針對提供者支援的語言，提供產生及編譯程式碼的方法。  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>使用 CodeDOM 程式碼提供者產生原始程式碼  
 若要以特定語言產生原始程式碼，您需要能代表要產生的原始程式碼結構的 CodeDOM 圖表。  
  
 以下範例示範如何建立 <xref:Microsoft.CSharp.CSharpCodeProvider> 的執行個體：  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 產生程式碼的圖表一般是包含在 <xref:System.CodeDom.CodeCompileUnit> 中。 若要為包含 CodeDOM 圖表的 **CodeCompileUnit** 產生程式碼，其中，請呼叫程式碼提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>方法。 此方法包含 <xref:System.IO.TextWriter> 用來產生原始程式碼的參數，因此有時候必須先建立可以寫入的 **TextWriter**。 以下範例示範從 **CodeCompileUnit** 產生程式碼，以及將產生的原始程式碼寫入名為 HelloWorld.cs 的檔案。  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>使用 CodeDOM 程式碼提供者編譯組件  
 **叫用編譯**  
  
 若要使用 CodeDom 提供者編譯組件，您必須有可以編譯器語言進行編譯的原始程式碼，或有可以產生要編譯之原始程式碼的 CodeDOM 圖表。  
  
 如要從 CodeDOM 圖表編譯，請將包含圖表的 <xref:System.CodeDom.CodeCompileUnit> 傳送至程式碼提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> 方法。 如果您有以編譯器了解的語言撰寫的原始程式碼檔案，請將包含原始程式碼的檔案名稱傳遞給 CodeDom 提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法。 您也可以將包含原始程式碼的字串 (此程式碼是以編譯器了解的語言撰寫)，傳遞到 CodeDom 提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> 方法。  
  
 **設定編譯參數**  
  
 CodeDom 提供者的所有標準編譯叫用方法都有一個類型為 <xref:System.CodeDom.Compiler.CompilerParameters> 的參數，指示編譯要使用的選項。  
  
 您可以在 **CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> 屬性中指定輸出組件的檔案名稱。 否則，會使用預設的輸出檔名稱。  
  
 根據預設，新的 **CompilerParameters** 是以其設為 **false** 的 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> 屬性初始化。 如要編譯可執行檔程式，**GenerateExecutable** 屬性必須設定為 **true**。 當 **GenerateExecutable** 設為 **false** 時，編譯器會產生類別庫。  
  
 如要從 CodeDOM 圖表編譯可執行檔，即必須在圖表中定義 <xref:System.CodeDom.CodeEntryPointMethod>。 如果有多個程式碼進入點，**CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A>屬性可能需要設定成類別名稱，定義要使用的進入點。  
  
 若要在產生的可執行檔中包含偵錯資訊，請將 <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> 屬性設為 **true**。  
  
 如果您的專案參考任何組件，組件名稱必須指定為 <xref:System.Collections.Specialized.StringCollection> 中的項目，當成叫用編譯時使用之 **CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> 屬性。  
  
 您可以將 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> 屬性設為 **true**，編譯寫入記憶體而非磁碟的組件。 當組件在記憶體中產生時，您的程式碼可從 <xref:System.CodeDom.Compiler.CompilerResults> 的 <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> 屬性取得所產生組件的參考。 如果組件寫入至磁碟，您可從 **CompilerResults** 的 <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A>屬性取得所產生組件的路徑。  
  
 若要在叫用編譯處理序時指定使用的自訂命令列引數字串，請在 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 屬性中設定字串。  
  
 如果需要 Win32 安全性權杖才能叫用編譯器處理序，請在 <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> 屬性中指定權杖。  
  
 若要將 Win32 資源檔連結至已編譯的組件，請在 <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> 屬性中指定 Win32 資源檔的名稱。  
  
 若要指定中斷編譯的警告層級，請將 <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> 屬性設為整數，表示要中斷編譯的警告層級。 您也可以將 <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> 屬性設成 **true**，設定編譯器在出現警告時中斷編譯。  
  
 下列程式碼範例示範使用衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別的 CodeDom 提供者編譯來源檔案。  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>初期支援的語言  
 .NET Framework 提供下列語言的程式碼編譯器和程式碼產生器：C#、Visual Basic、C++ 和 JScript。 實作特定語言的程式碼產生器和程式碼編譯器，即可擴充 CodeDOM 對其他語言的支援。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [動態原始程式碼的產生和編譯](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [CodeDOM 快速參考](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
