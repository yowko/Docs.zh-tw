---
title: "動態原始程式碼的產生和編譯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535a60aa1a174319a4db3403a64c3998784bbb58
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="dynamic-source-code-generation-and-compilation"></a>動態原始程式碼的產生和編譯
.NET Framework 包含稱為程式碼文件物件模型 (CodeDOM) 的機制，它可讓發出原始程式碼的程式開發人員在執行階段，根據代表要呈現之程式碼的單一模型，產生多種程式語言的原始程式碼。  
  
 為了代表原始程式碼，CodeDOM 項目會彼此連結，形成稱為 CodeDOM 圖形的資料結構，它會建立一些原始程式碼結構的模型。  
  
 `System.CodeDom` 命名空間會定義類型，可代表獨立於特定程式設計語言的原始碼邏輯結構。 `System.CodeDom.Compiler` 命名空間會定義類型，以從 CodeDOM 圖表產生原始程式碼，以及管理使用支援語言的原始程式碼編譯。 編譯器廠商或開發人員可以擴充支援的語言集。  
  
 程式需要產生適用於多種語言的程式模型原始程式碼，或是不確定目標語言的原始程式碼時，很適合使用與語言無關的原始程式碼模型。 比方說，某些設計工具使用 CodeDOM 作為語言抽象介面，以正確的程式設計語言產生程式碼，如果該語言支援 CodeDOM 的話。  
  
 .NET Framework 包含 <xref:Microsoft.CSharp.CSharpCodeProvider>、<xref:Microsoft.JScript.JScriptCodeProvider> 和 <xref:Microsoft.VisualBasic.VBCodeProvider> 的程式碼產生器和程式碼編譯器。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 說明常見的用法，並示範使用 CodeDOM 建置簡單的物件圖形。  
  
 [從 CodeDOM 圖表產生原始程式碼和編譯程式](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 描述如何產生原始程式碼，和使用外部編譯器以及 `System.CodeDom.Compiler` 命名空間中定義的類別編譯產生的程式碼。  
  
 [如何：使用 CodeDOM 建立 XML 文件檔案](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 描述如何使用 CodeDOM 產生程式碼和 XML 文件註解，並編譯產生的程式碼，以建立 XML 文件輸出。  
  
 [如何：使用 CodeDOM 建立類別](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 描述如何使用 CodeDOM 產生包含欄位、屬性、方法、建構函式和進入點的類別。  
  
## <a name="reference"></a>參考資料  
 <xref:System.CodeDom>  
 定義元素，代表以 Common Language Runtime 為目標之程式設計語言中的程式碼元素。  
  
 <xref:System.CodeDom.Compiler>  
 定義介面以便在執行階段產生和編譯程式碼。  
  
## <a name="related-sections"></a>相關章節  
 [CodeDOM 快速參考](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 提供快速方法，讓開發人員尋找代表原始程式碼元素的 CodeDOM 元素。
