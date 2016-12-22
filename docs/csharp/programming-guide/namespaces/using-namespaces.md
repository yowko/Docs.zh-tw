---
title: "使用命名空間 (C# 程式設計手冊) | Microsoft Docs"
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
  - "cs.names"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "完整名稱 [C#]"
  - "命名空間 [C#], 使用方法"
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 使用命名空間 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 程式大量使用命名空間有兩個原因。  第一，.NET Framework 類別會使用命名空間組織其多種類別。  第二，宣告您自己的命名空間，可以幫助您在較大型的程式設計專案中控制類別和方法名稱的範圍。  
  
## 存取命名空間  
 大部分的 C\# 應用程式以使用 `using` 指示詞的區段做為開頭。  這個區段會列出應用程式經常使用的命名空間，這樣一來，程式設計人員每次使用其中的方法時，就不需要再指定完整名稱。  
  
 例如，在程式的開頭加入這一行：  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 程式設計人員可以使用以下程式碼：  
  
 [!code-cs[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 取代以下程式碼：  
  
 [!code-cs[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## 命名空間別名  
 [using 指示詞](../../../csharp/language-reference/keywords/using-directive.md) 也可以用來建立[命名空間](../../../csharp/language-reference/keywords/namespace.md)的別名。  例如，如果要使用先前所撰寫的命名空間，且其中包含巢狀命名空間，您可能就要宣告別名，以快速參考特定命名空間，如下列範例所示：  
  
 [!code-cs[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## 使用命名空間控制範圍  
 `namespace` 關鍵字的用途在於宣告範圍。  能夠在專案中建立範圍，有助於您組織程式碼並建立全域唯一型別。  在下列範例中，`SampleClass` 的類別會分別在兩個命名空間中定義，其中一個命名空間以巢狀方式置於另一個中。  [. 運算子](../../../csharp/language-reference/operators/member-access-operator.md) 可用來區分要呼叫哪一個方法。  
  
 [!code-cs[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## 完整名稱  
 命名空間和型別具有唯一名稱，而這個名稱是由表示邏輯階層架構的完整名稱所描述。  例如，陳述式 `A.B` 代表 `A` 是命名空間或型別的名稱，而 `B` 是以巢狀方式置於其內部。  
  
 下面範例中便具有巢狀的類別和命名空間。  每一實體後的註解代表完整的名稱。  
  
 [!code-cs[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 在先前的程式碼片段中：  
  
-   `N1` 命名空間是全域命名空間的一個成員。  其完整名稱是 `N1`。  
  
-   `N2` 命名空間是 `N1` 的一個成員。  其完整名稱是 `N1.N2`。  
  
-   `C1` 類別是 `N1` 的一個成員。  其完整名稱是 `N1.C1`。  
  
-   這段程式碼中用了兩次 `C2` 類別名稱，  但是該完整名稱仍具唯一獨特性。  第一個 `C2` 執行個體是在 `C1` 內宣告，因此其完整名稱為 `N1.C1.C2`。  第二個 `C2` 執行個體是在 `N2` 命名空間內宣告，因此其完整名稱為 `N1.N2.C2`。  
  
 您可以使用之前的程式碼片段，將新的類別成員 `C3` 加入 `N1.N2` 命名空間中，如下所示：  
  
 [!code-cs[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 一般來說，會使用 `::` 參考命名空間別名，或使用 `global::` 參考全域命名空間，以及使用 `.` 限定型別或成員。  
  
 將 `::` 與參考型別的別名一起使用會造成錯誤，應與參考命名空間的別名一起使用才正確。  例如：  
  
 [!code-cs[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-cs[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 請注意，`global` 一字並不是預先定義的別名，因此 `global.X` 並沒有任何特殊意義。  只有在與 `::` 一起使用時，這個字才會有特殊的意義。  
  
 如果您定義名為 global 的別名就會產生編譯器警告 CS0440，因為 `global::` 一定會參考全域命名空間而非別名。  例如，下列的程式行會產生警告：  
  
 [!code-cs[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 將 `::` 與別名一起使用是很好的方式，並且可以避免未預期地加入其他型別。  例如，請考慮下列程式碼範例：  
  
 [!code-cs[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-cs[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 這種方式可以運作，但是如果往後加入名為 `Alias` 的型別，`Alias.` 就會繫結至該型別。  使用 `Alias::Exception` 確保將 `Alias` 視為命名空間別名，而不會誤認為型別。  
  
 如需 `global` 別名的詳細資訊，請參閱 [如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) 主題。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [命名空間](../../../visual-basic/reference/command-line-compiler/index.md)   
 [命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [. 運算子](../../../csharp/language-reference/operators/member-access-operator.md)   
 [:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)