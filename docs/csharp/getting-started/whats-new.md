---
title: "What&#39;s New for Visual C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9f18dc26-27fa-4603-a639-b573f07a117b
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# What&#39;s New for Visual C# #
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

本頁列出每個 C\# 版本的主要功能名稱，並說明該語言最新版本的新功能和增強功能。  
  
## 舊版本  
 C\# 1 \/ Visual Studio .NET 2002  
 初次發行  
  
 C\# 1.1 \/ Visual Studio .NET 2003  
 `#line` pragma 和 XML 文件註解  
  
 C\# 2 \/ Visual Studio .NET 2005  
 匿名方法、泛型、可為 Null 的類型、迭代器\/yield、`static` 類別、委派的共變數\/反變數  
  
 C\# 3 \/ Visual Studio .NET 2008  
 物件和集合初始設定式、Lambda 運算式、擴充方法、匿名類型、自動屬性、Language Integrated Query \(LINQ\)、匿名類型、區域 `var` 類型推斷、LINQ  
  
 C\# 4 \/ Visual Studio .NET 2010  
 `Dynamic`、具名引數、選擇性參數、泛型共變數\/反變數  
  
 C\# 5 \/ Visual Studio .NET 2012  
 `Async` \/ `await`、呼叫端資訊屬性  
  
 Visual Studio .NET 2013  
 .NET 編譯器平台 \("Roslyn"\) 的 Bug 修正、效能提升和技術預覽  
  
 C\# 6 \/ Visual Studio .NET 2015  
 目前的版本 \(如下所示\)  
  
## 目前的版本  
 [nameof](../../csharp/language-reference/keywords/nameof.md)  
 您可以取得用於錯誤訊息之類型或成員的未限定字串名稱，而不需要對字串進行硬式編碼。  這可讓您的程式碼在重構時保持正確。  這項功能也可用來連接模型檢視控制器 MVC 連結，以及引發屬性已變更事件。  
  
 [字串插值](../../csharp/language-reference/keywords/interpolated-strings.md)  
 您可以使用字串插值運算式來建構字串。  字串插值運算式類似包含運算式的範本字串。  C\# 會透過以運算式結果的 ToString 表示取代運算式，來建立字串。  對於引數而言，字串插值比[複合格式](../Topic/Composite%20Formatting.md)更容易了解。  
  
 [Null 條件式成員存取和索引](../../csharp/language-reference/operators/null-conditional-operators.md)  
 您可以在執行成員存取 \(`?.`\) 或對 \(`?[]`\) 作業編製索引之前，透過非常精簡的語法來測試是否為 Null。  這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。  如果左運算元或物件參考為 Null，則作業會傳回 Null。  
  
 [索引初始設定式](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 您現在可以初始化集合中支援索引的特定項目，例如初始化字典。  
  
 [集合初始設定式和加入擴充方法](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 現在當集合有加入擴充方法時，您可以使用初始設定式進行收集。  之前，加入方法必須是執行個體方法。  
  
 **多載解析**  
 編譯器已改進多載解析，可產生更多運作如您預期的程式碼。  在採用可為 Null 的實值類型的多載之間進行選擇時，或在將方法群組 \(而不是 Lambda\) 傳遞至採用委派的多載時，可能不會再出現問題。  
  
 [例外狀況篩選條件](../../csharp/language-reference/keywords/try-catch.md)  
 您可以在 `catch` 子句中使用例外狀況篩選條件，以判斷 Catch 子句是否應該處理例外狀況。  如果沒有這項功能，您必須重新擲回例外狀況，以裁剪重新擲回之例外狀況所回報的呼叫堆疊。  
  
 [Catch 和 Finally 區塊中的 Await](../../csharp/language-reference/keywords/try-catch.md)  
 您可以在 `catch` 和 `finally` 子句中使用 `await`。  
  
 [Auto 屬性初始設定式](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 您現在可以使用初始化欄位的類似方式，來初始化 Auto 屬性。  
  
 [僅限 Getter 的 Auto 屬性](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 您現在可以定義唯讀 Auto 屬性，而不需要使用完整的屬性語法來定義屬性。  您可以在宣告屬性的位置或類型的建構函式中，初始化屬性。  
  
 **具有運算式主體的函式成員**  
 您可以使用用於 Lambda 運算式的相同輕量型語法，來宣告具有程式碼運算式主體的成員。  請參閱[方法](../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../csharp/programming-guide/classes-and-structs/properties.md)、[索引子](../../visual-basic/reference/command-line-compiler/index.md)和[多載運算子](../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)。  
  
 [使用靜態](../../csharp/language-reference/keywords/using-directive.md)  
 您可以匯入靜態類型的可存取靜態成員，以便參考成員，而不需要用類型的名稱來限定存取。  
  
## 請參閱  
 [Visual Studio 2015 的新功能](/visual-studio/ide/what-s-new-in-visual-studio-2015)