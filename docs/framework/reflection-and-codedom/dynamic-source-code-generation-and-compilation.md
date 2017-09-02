---
title: "動態原始程式碼的產生和編譯 | Microsoft Docs"
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
  - "程式碼文件物件模型"
  - "CodeDOM"
  - "與語言無關的原始程式碼模型"
  - "語言, CodeDOM 支援的多個語言"
  - "CodeDOM 支援的多個語言"
  - "多個語言的原始程式碼"
  - "System.CodeDom 命名空間"
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 動態原始程式碼的產生和編譯
.NET Framework 包括一種名為程式碼文件物件模型 \(CodeDOM\) 的機制，可以讓發出原始程式碼的程式開發人員在執行階段時，依據代表要轉譯之程式碼的單一模型，使用多種程式語言來產生原始程式碼。  
  
 為了表示原始程式碼，CodeDOM 項目彼此連結以形成名為 CodeDOM 物件 Graph 的資料結構，這就是某些原始程式碼的結構模型。  
  
 `System.CodeDom` 命名空間定義的型別可以表示原始程式碼的邏輯結構，不限定於特定的程式語言。  `System.CodeDom.Compiler` 命名空間定義的型別會從 CodeDOM 圖形產生原始程式碼，並在支援的語言中管理原始程式碼的編譯。  編譯器廠商或開發人員可以擴充支援的語言集合。  
  
 程式需要為使用多種語言中的程式模型或不確定的目標語言產生原始程式碼時，與語言無關的原始程式碼模型就非常有用。  例如，如果該語言有 CodeDOM 支援，有些設計人員會使用 CodeDOM 做為語言抽象介面以在正確的程式語言中產生原始程式碼。  
  
 .NET Framework 包含了 [C\#](frlrfMicrosoftCSharpCSharpCodeProviderClassTopic)、[JScript](frlrfMicrosoftJScriptJScriptCodeProviderClassTopic) 和 [Visual Basic](frlrfMicrosoftVisualBasicVBCodeProviderClassTopic) 所適用的程式碼產生器和程式碼編譯器。  
  
## 在本節中  
 [使用 CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 描述一般的運用，並且示範使用 CodeDOM 建置簡單的物件 Graph。  
  
 [從 CodeDOM 物件 Graph 產生原始程式碼和編譯程式](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 描述如何產生原始程式碼，並使用 `System.CodeDom.Compiler` 命名空間中定義的類別來以外部編譯器編譯產生的程式碼。  
  
 [如何：使用 CodeDOM 建立 XML 文件檔案](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 說明如何使用 CodeDOM 來產生具有 XML 文件註解的程式碼，並編譯產生的程式碼，使其建立 XML 文件輸出。  
  
 [如何：使用 CodeDOM 建立類別](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 說明如何使用 CodeDOM 來產生包含欄位、屬性、方法、建構函式 \(Constructor\) 和進入點的類別。  
  
## 參考  
 <xref:System.CodeDom>  
 定義一些項目來表示以 Common Language Runtime 為目標之程式語言中的程式碼項目。  
  
 <xref:System.CodeDom.Compiler>  
 定義在執行階段用於產生和編譯程式碼的介面。  
  
## 相關章節  
 [CodeDOM Quick Reference](http://msdn.microsoft.com/zh-tw/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 為開發人員提供快速方法，找出表示原始程式碼項目的 CodeDOM 項目。