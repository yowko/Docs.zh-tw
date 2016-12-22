---
title: "外部別名 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "alias_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "別名 [C#], extern 關鍵字"
  - "別名, extern 關鍵字"
  - "extern alias 關鍵字 [C#]"
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 外部別名 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可能需要參考具有相同完整型別名稱的兩個組件 \(Assembly\) 版本。  例如，您可能需要在相同的應用程式中，使用某組件的兩個或更多個版本。  藉由使用外部組件別名 \(Alias\)，來自每個組件的命名空間 \(Namespace\) 可包裝在別名所命名的根層級命名空間內，這樣即可讓它們在相同的檔案中使用。  
  
> [!NOTE]
>  [extern](../../../csharp/language-reference/keywords/extern.md) 關鍵字還可當做方法修飾詞使用，用於宣告以 Unmanaged 程式碼撰寫的方法。  
  
 若要參考兩個擁有相同完整型別名稱的組件，則必須在命令提示字元上指定別名，如下所示：  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 這將建立 `GridV1` 和 `GridV2` 等兩個外部別名。  若要從程式內使用這些別名，請使用 `extern` 關鍵字來參考它們。  例如：  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 每個外部別名宣告會另外採用與全域命名空間平行但不在其內的根層次命名空間。  因此，來自各組件的型別可利用它們的完整名稱 \(起源於適當的命名空間別名\) 來正確參考  
  
 在上述範例中，`GridV1::Grid` 會是來自 `grid.dll` 的方格控制項，`GridV2::Grid` 則會是來自 `grid20.dll` 的方格控制項。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)