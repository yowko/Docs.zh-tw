---
title: 使用建構函式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 14ff272fe940c265dc8984d6b20985bb2d2ba12d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398256"
---
# <a name="using-constructors-c-programming-guide"></a>使用建構函式 (C# 程式設計手冊)

建立[類別](../../../csharp/language-reference/keywords/class.md)或[結構](../../../csharp/language-reference/keywords/struct.md)時，會呼叫其建構函式。 建構函式的名稱與類別或結構相同，而且通常會初始化新物件的資料成員。  
  
 在下列範例中，使用一個簡單的建構函式定義名為 `Taxi` 的類別。 然後使用 [new](../../../csharp/language-reference/operators/new-operator.md) 運算子具現化此類別。 為新物件配置記憶體之後，`new` 運算子會立即叫用 `Taxi` 建構函式。  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 不接受任何參數的建構函式稱為「無參數建構函式」  。 每當使用 `new` 運算子來具現化物件，而且未提供引數給 `new` 時，便會叫用預設建構函式。 如需詳細資訊，請參閱[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。  
  
 除非類別是[靜態](../../../csharp/language-reference/keywords/static.md)，否則沒有建構函式的類別會從 C# 編譯器取得一個公開無參數建構函式，以啟用類別具現化。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 您可以將建構函式設為私用，避免具現化類別，如下所示：  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 如需詳細資訊，請參閱 [私用建構函式](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)。  
  
 [結構](../../../csharp/language-reference/keywords/struct.md)型別的建構函式與類別建構函式相似，但 `structs` 無法包含明確的無參數建構函式，因為編譯器會自動提供一個。 此建構函式會將 `struct` 中的每個欄位都初始化為預設值。 如需詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。 但是，這個無參數建構函式只會在使用 `new` 具現化 `struct` 時叫用。 例如，此程式碼使用 <xref:System.Int32> 的無參數建構函式，因此您可以保證該整數已進行初始化：  
  
```csharp  
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
  
 因此您不需要呼叫實值型別的無參數建構函式。  
  
 類別和 `structs` 都可以定義使用參數的建構函式。 使用參數的建構函式必須透過 `new` 陳述式或 [base](../../../csharp/language-reference/keywords/base.md) 陳述式呼叫。 類別和 `structs` 也可以定義多個建構函式，且皆無須定義無參數建構函式。 例如：  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 使用下列任一陳述式即可建立此類別：  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 建構函式可以使用 `base` 關鍵字呼叫基底類別的建構函式。 例如：  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 在此範例中，執行建構函式的區塊之前，會先呼叫基底類別的建構函式。 不論是否有參數，都可以使用 `base` 關鍵字。 建構函式的任何參數都可以作為 `base` 的參數使用，或作為運算式的一部分使用。 如需詳細資訊，請參閱 [base](../../../csharp/language-reference/keywords/base.md)。  
  
 在衍生類別中，如果未使用 `base` 關鍵字明確呼叫基底類別建構函式，則會隱含呼叫無參數建構函式 (如果有)。 這表示下列建構函式宣告的作用相同：  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 如果基底類別未提供無參數建構函式，衍生類別就必須使用 `base` 明確呼叫基底建構函式。  
  
 建構函式可以使用 [this](../../../csharp/language-reference/keywords/this.md) 關鍵字來叫用相同物件中的另一個建構函式。 如同 `base`，不論是否有參數，都可以使用 `this`，而且建構函式中的任何參數都可以作為 `this` 的參數使用，或作為運算式的一部分使用。 例如，上述範例中的第二個建構函式可使用 `this` 重寫成：  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 在上述範例中使用 `this` 會呼叫下列建構函式：  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 建構函式可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md) 或 [private protected](../../../csharp/language-reference/keywords/private-protected.md)。 這些存取修飾詞定義類別使用者如何建構類別。 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 建構函式可使用 [static](../../../csharp/language-reference/keywords/static.md) 關鍵字宣告為靜態。 靜態建構函式會在即將存取任何靜態欄位之前自動進行呼叫，而且通常會用來初始化靜態類別成員。 如需詳細資訊，請參閱[靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[執行個體建構函式](~/_csharplang/spec/classes.md#instance-constructors)和[靜態建構函式](~/_csharplang/spec/classes.md#static-constructors)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)
- [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)
