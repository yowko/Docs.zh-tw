---
title: "使用建構函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "建構函式 [C#], 關於建構函式"
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# 使用建構函式 (C# 程式設計手冊)
在 [類別](../../../csharp/language-reference/keywords/class.md) 或 [結構](../../../csharp/language-reference/keywords/struct.md) 建立時，它的建構函式呼叫。  建構函式的名稱與類別或結構相同，因此，它們通常用來初始化新物件的資料成員。  
  
 下列範例將使用簡單的建構函式來定義名為 `Taxi` 的類別。  然後再用 [new](../../../csharp/language-reference/keywords/new.md) 運算子執行個體化此類別。  為新物件配置記憶體之後，`new` 運算子會叫用 `Taxi` 建構函式。  
  
 [!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_1.cs)]  
  
 不使用任何參數的建構函式稱為「*預設建構函式*」\(Default Constructor\)。  每當使用 `new` 運算子來具現化物件，而且未提供引數給 `new` 時，便會叫用預設建構函式。  如需詳細資訊，請參閱[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。  
  
 除非是[靜態](../../../csharp/language-reference/keywords/static.md)類別，否則只要是沒有建構函式的類別，C\# 編譯器都會指定公用 \(Public\) 預設建構函式，以執行類別執行個體化。  如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 您可以將建構函式設為私用 \(Private\)，避免執行個體化類別，如下所示：  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_2.cs)]  
  
 如需詳細資訊，請參閱[私用建構函式](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)。  
  
 [結構](../../../csharp/language-reference/keywords/struct.md)型別的建構函式與類別建構函式類似，但是 `structs` 不能包含明確的預設建構函式，因為編譯器已經自動提供一個預設建構函式。  這個建構函式會將 `struct` 中的每個欄位都初始化為預設值。  如需詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  不過，只有當 `struct` 是用 `new` 具現化時，才會叫用這個預設建構函式。  例如，這段程式碼會使用 <xref:System.Int32> 的預設建構函式，因此您可以確定整數已加以初始化：  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 然而下列程式碼會導致編輯器錯誤，因為程式碼沒有使用 `new`，而且嘗試使用尚未初始化的物件：  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 或者，以 `structs` 為基礎的物件 \(包括所有內建的實值型別\) 都可以初始化或指派然後使用，如同下列範例中所示：  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 因此不需要呼叫實值型別的預設建構函式。  
  
 類別和 `structs` 都可以定義使用參數的建構函式。  必須透過 `new` 陳述式或[基底](../../../csharp/language-reference/keywords/base.md)陳述式來呼叫使用參數的建構函式。  類別和 `structs` 也可以定義多個建構函式，而且都不必定義預設建構函式。  例如：  
  
 [!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_3.cs)]  
  
 使用下列其中一個陳述式即可建立這個類別：  
  
 [!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_4.cs)]  
  
 建構函式可以使用 `base` 關鍵字呼叫基底類別的建構函式。  例如：  
  
 [!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_5.cs)]  
  
 在這個範例中，執行建構函式的區塊之前，會先呼叫基底類別的建構函式。  無論是否有參數，都可以使用 `base` 關鍵字。  建構函式的任何參數都可以當做 `base` 的參數或運算式的一部分來使用。  如需詳細資訊，請參閱[base](../../../csharp/language-reference/keywords/base.md)。  
  
 在衍生類別 \(Derived Class\) 中，如果沒有使用 `base` 關鍵字明確呼叫基底類別建構函式，便會隱含呼叫基底類別建構函式 \(如果存在的話\)。  這表示下列建構函式宣告的作用相同：  
  
 [!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_6.cs)]  
  
 [!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_7.cs)]  
  
 如果基底類別未提供預設建構函式，衍生類別就必須使用 `base` 明確呼叫基底建構函式。  
  
 建構函式可以使用 [this](../../../csharp/language-reference/keywords/this.md) 關鍵字來叫用相同物件中的另一個建構函式。  如同 `base` 一樣，無論是否有參數，都可以使用 `this`，而且建構函式中的任何參數都可以當做 `this` 的參數或運算式的一部分。  例如，在先前範例中的第二個建構函式，可以使用 `this` 重新撰寫成：  
  
 [!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_8.cs)]  
  
 在上述範例中使用 `this` 關鍵字，會造成必須呼叫這個建構函式：  
  
 [!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_9.cs)]  
  
 建構函式可標示為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected` `internal`。  這些存取修飾詞 \(Modifier\) 將定義類別使用者如何建構類別。  如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 建構函式可使用 [static](../../../csharp/language-reference/keywords/static.md) 關鍵字宣告為靜態。  靜態建構函式會在即將存取任何靜態欄位之前自動進行呼叫，而靜態建構函式通常是用來初始化靜態類別成員。  如需詳細資訊，請參閱[靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)