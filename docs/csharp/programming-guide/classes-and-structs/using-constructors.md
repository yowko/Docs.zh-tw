---
title: "使用建構函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9d61870e6d2d8f905c56f86bbb6e6d99d5dae80c
ms.lasthandoff: 03/13/2017

---
# <a name="using-constructors-c-programming-guide"></a>使用建構函式 (C# 程式設計手冊)
建立[類別](../../../csharp/language-reference/keywords/class.md)或[結構](../../../csharp/language-reference/keywords/struct.md)時，會呼叫其建構函式。 建構函式的名稱與類別或結構相同，而且通常會初始化新物件的資料成員。  
  
 在下列範例中，使用一個簡單的建構函式定義名為 `Taxi` 的類別。 然後使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子具現化此類別。 為新物件配置記憶體之後，`new` 運算子會立即叫用 `Taxi` 建構函式。  
  
 [!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 不使用任何參數的建構函式稱為*「預設建構函式」*。 每當使用 `new` 運算子來具現化物件，而且未提供引數給 `new` 時，便會叫用預設建構函式。 如需詳細資訊，請參閱[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。  
  
 除非是[靜態](../../../csharp/language-reference/keywords/static.md)類別，否則只要是沒有建構函式的類別，C# 編譯器都會指定公用預設建構函式，以啟用類別具現化。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 您可以將建構函式設為私用，避免具現化類別，如下所示：  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 如需詳細資訊，請參閱 [私用建構函式](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)。  
  
 [結構](../../../csharp/language-reference/keywords/struct.md)類型的建構函式與類別建構函式類似，但 `structs` 不能包含明確的預設建構函式，因為編譯器已自動提供一個預設建構函式。 此建構函式會將 `struct` 中的每個欄位都初始化為預設值。 如需詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。 不過，只有 `struct` 是以 `new` 具現化時，才會呼叫此預設建構函式。 例如，下列程式碼使用 <xref:System.Int32> 的預設建構函式，因此您可以確定整數已加以初始化：  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 不過，下列程式碼由於未使用 `new`，而且會嘗試使用尚未初始化的物件，因此會造成編譯器錯誤：  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 或者，您可以初始化或指派以 `structs` 為基礎的物件 (包括所有內建數字類型)，再如下列範例所示使用這些物件：  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 因此不需要呼叫實值型別的預設建構函式。  
  
 類別和 `structs` 都可以定義使用參數的建構函式。 使用參數的建構函式必須透過 `new` 陳述式或 [base](../../../csharp/language-reference/keywords/base.md) 陳述式呼叫。 類別和 `structs` 也可以定義多個建構函式，而且都不必定義預設建構函式。 例如:   
  
 [!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 使用下列任一陳述式即可建立此類別：  
  
 [!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 建構函式可以使用 `base` 關鍵字呼叫基底類別的建構函式。 例如:   
  
 [!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 在此範例中，執行建構函式的區塊之前，會先呼叫基底類別的建構函式。 不論是否有參數，都可以使用 `base` 關鍵字。 建構函式的任何參數都可以作為 `base` 的參數使用，或作為運算式的一部分使用。 如需詳細資訊，請參閱 [base](../../../csharp/language-reference/keywords/base.md)。  
  
 在衍生類別中，如果未使用 `base` 關鍵字明確呼叫基底類別建構函式，則會隱含呼叫預設建構函式 (如果有)。 這表示下列建構函式宣告的作用相同：  
  
 [!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 如果基底類別未提供預設建構函式，衍生類別就必須使用 `base` 明確呼叫基底建構函式。  
  
 建構函式可以使用 [this](../../../csharp/language-reference/keywords/this.md) 關鍵字來叫用相同物件中的另一個建構函式。 如同 `base`，不論是否有參數，都可以使用 `this`，而且建構函式中的任何參數都可以作為 `this` 的參數使用，或作為運算式的一部分使用。 例如，上述範例中的第二個建構函式可使用 `this` 重寫成：  
  
 [!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 在上述範例中使用 `this` 會呼叫下列建構函式：  
  
 [!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 建構函式可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected``internal`。 這些存取修飾詞定義類別使用者如何建構類別。 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 建構函式可使用 [static](../../../csharp/language-reference/keywords/static.md) 關鍵字宣告為靜態。 靜態建構函式會在即將存取任何靜態欄位之前自動進行呼叫，而且通常會用來初始化靜態類別成員。 如需詳細資訊，請參閱[靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)
