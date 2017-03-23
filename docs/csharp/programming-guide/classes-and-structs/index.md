---
title: "類別和結構 (C# 程式設計手冊) | Microsoft Docs"
description: Describes the use of classes and structures (structs) in C#.
ms.date: "2016-01-17"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 類別"
  - "C# 語言, 物件"
  - "C# 語言, 結構"
  - "類別 [C#], 概觀"
  - "物件 [C#]"
  - "結構 [C#], 關於結構"
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
caps.latest.revision: 48
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 48
---
# 類別和結構 (C# 程式設計手冊)
類別 \(Class\) 和結構 \(Struct\) 是 .NET Framework 一般類型系統中的兩個基本建構。  這兩個本質上都是資料結構 \(Structure\)，封裝了一整組資料和行為以組成邏輯單元。  資料和行為是類別或結構的「*成員*」\(Member\)，各自包含自己的方法、屬性和事件等，本主題稍後會列出。  
  
 類別或結構宣告就像是藍圖，用於建立執行階段的執行個體 \(Instance\) 或物件。  如果您定義名為 `Person` 的類別或結構，`Person` 就是類型的名稱。  如果您宣告並初始化變數 `p` 為類型 `Person`，則 `p` 就是 `Person` 的物件或執行個體。  同一個 `Person` 類型可以建立多個執行個體，而每個執行個體的屬性和欄位可以有不同的值。  
  
 類別是「參考類型」\(Reference Type\)。  建立類別的物件時，物件所指派的變數僅持有該記憶體的參考。  將物件參考指派給新變數時，新變數會參考原始物件。  對其中一個變數進行的變更，會反映到另一個變數中，因為這兩個變數參考相同資料。  
  
 結構是實值類型 \(Value Type\)。  建立結構時，結構所指派的變數會持有結構的實際資料。  將結構指派給新變數時，會進行複製。  因此，新變數和原始變數總共包含兩份相同資料的不同複本。  對其中一份複本進行的變更，不會影響另一份複本。  
  
 一般而言，類別是針對更複雜的行為或在類別物件建立後計劃用於修改的資料，用來塑造它們的模型。  結構 \(Struct\) 則最適合小型資料結構 \(Structure\)，其中包含的主要資料在結構 \(Struct\) 建立後並不計劃加以修改。  
  
 如需詳細資訊，請參閱 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)、[物件](../../../csharp/programming-guide/classes-and-structs/objects.md)和[結構](../../../csharp/programming-guide/classes-and-structs/structs.md)。  
  
## 範例  
 以下範例會定義 `MyCustomClass`，其中包含 `ProgrammingGuide` 命名空間最上層的三個成員。  `MyCustomClass` 的執行個體 \(物件\) 是在 `Program` 類別的 `Main` 方法中定義，且物件的方法和屬性可使用點標記法存取。  
  
 [!code-cs[csProgGuideObjects#88](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_1.cs)]  
  
## 封裝  
 「*封裝*」\(Encapsulation\) 有時候被稱為物件導向程式設計的第一個支柱或原則。  根據封裝原則，類別或結構可以指定類別或結構外部的程式碼對於它們的每一個成員有多少存取範圍。  不計劃用在類別或組件 \(Assembly\) 外部的方法和變數可以加以隱藏，以降低程式碼錯誤或惡意擅用的可能。  
  
 如需類別的詳細資訊，請參閱[類別](../../../csharp/programming-guide/classes-and-structs/classes.md) 和[物件](../../../csharp/programming-guide/classes-and-structs/objects.md)。  
  
### Members  
 所有方法、欄位、常數、屬性和事件都必須在類型中加以宣告，這些即稱為類型的「*成員*」\(Member\)。  C\# 中沒有全域變數或方法，而在其他語言中則有。  就算是程式的進入點 `Main` 方法，也必須在類別或結構中加以宣告。  下列清單包含可在類別或結構中宣告的所有不同類型成員。  
  
-   [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [常數](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [事件](../../../csharp/programming-guide/events/index.md)  
  
-   [索引子](../../../csharp/programming-guide/indexers/index.md)  
  
-   [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [巢狀類型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### 協助工具  
 有些方法和屬性適用於從類別或結構外部的程式碼進行呼叫或存取，此稱為「*用戶端程式碼*」\(Client Code\)。  其他方法和屬性則可能僅適用於類別或結構本身。  所以，請務必限制您的程式碼的存取範圍，只開放給計劃中的用戶端程式碼。  請使用存取修飾詞 \(Modifier\) [public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、`protected internal` 和 [private](../../../csharp/language-reference/keywords/private.md)，為類型及其成員指定用戶端程式碼對它們的存取程度。  預設存取範圍為 `private`。  如需詳細資訊，請參閱 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
### 繼承  
 類別 \(非結構\) 支援繼承概念。  繼承自另一個類別 \(「*基底類別*」\(Base Class\)\) 的類別會自動包含基底類別的所有 public、protected 和 internal 成員，但不包括其建構函式和解構函式。  如需詳細資訊，請參閱 [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)和 [多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)。  
  
 類別可宣告為[抽象](../../../csharp/language-reference/keywords/abstract.md)，表示其中一個或多個方法沒有實作。  即使抽象類別無法直接執行個體化，仍可做為其他提供遺漏實作之類別的基底類別。  類別還可以宣告為[密封](../../../csharp/language-reference/keywords/sealed.md)，必免其他類別從中繼承。  如需詳細資訊，請參閱 [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
### 介面  
 類別和結構可繼承多個介面。  繼承自介面表示該類型實作介面中定義的所有方法。  如需詳細資訊，請參閱 [介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
### 泛型類型  
 類別和結構可使用一個或多個類型參數定義。  用戶端程式碼會在建立類型的執行個體時提供類型。  例如，<xref:System.Collections.Generic> 命名空間中的 <xref:System.Collections.Generic.List%601> 類別會以一個類型參數定義。  用戶端程式碼會建立 `List<string>` 或 `List<int>` 的執行個體，指定清單將擁有的類型。  如需詳細資訊，請參閱 [泛型](../../../csharp/programming-guide/generics/index.md)。  
  
### 靜態類型  
 類別 \(而不是結構\) 可以宣告為[靜態](../../../csharp/language-reference/keywords/static.md)。  靜態類別只能包含靜態成員，且不可使用 new 關鍵字執行個體化。  程式載入時，會將一個類別副本載入至記憶體中，而且其成員可透過類別名稱存取。  類別和結構都可以包含靜態成員。  如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
### 巢狀類型  
 類別或結構也可以透過巢狀方式置於其他類別或結構中。  如需詳細資訊，請參閱[巢狀類型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)。  
  
### 部分類型  
 您可以在某個程式碼檔案中定義類別、結構或方法的一部分，並且在另一個程式碼檔案中定義另一個部分。  如需詳細資訊，請參閱[部分類別定義 \(C\# 程式設計手冊\)](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
### 物件初始設定式  
 您可以執行個體化和初始化類別或結構物件，以及物件集合，而不需明確呼叫其建構函式。  如需詳細資訊，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
### 匿名類型  
 在不方便或不需要建立具名類別的情況下，例如使用不需要永久保存或傳遞至另一個方法的資料結構填入清單時，可以使用匿名類型。  如需詳細資訊，請參閱[匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
### 擴充方法  
 您可以透過建立其方法可如同屬於原始類型一般呼叫的另一個類別，藉此「擴充」類別而不需建立衍生的類別。  如需詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  
  
### 隱含類型區域變數  
 在類別或結構方法內，您可以使用隱含類型建構編譯器，以判斷編譯時期的正確類型。  如需詳細資訊，請參閱[隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)