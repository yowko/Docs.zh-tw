---
title: 類別 (C# 程式設計手冊)
description: 了解類別類型和其建立方式
ms.date: 04/05/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1909623d3d8f6110a5fb466575bdab2d45495c2a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="classes-c-programming-guide"></a>類別 (C# 程式設計手冊)
「類別」是一種建構，可讓您將其他類型、方法和事件的變數群組在一起，以建立您自己的自訂類型。 類別就像藍圖。 它會定義類型的資料和行為。 如果類別未宣告為靜態，則用戶端程式碼可以建立它的「執行個體」。 這些執行個體是指派給變數的「物件」。 除非類別的執行個體的所有參考都超出範圍，否則變數會保留在記憶體中。 此時，CLR 會將它標記為適合進行記憶體回收。 如果類別宣告為 [static](../../../csharp/language-reference/keywords/static.md)，則您無法建立執行個體，而且用戶端程式碼只能透過類別本身存取它。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  

## <a name="reference-types"></a>參考型別  
定義為 [class](../../../csharp/language-reference/keywords/class.md) 的類型即為「參考型別」。 在執行階段，當您宣告參考型別的變數時，該變數會包含值 [null](../../../csharp/language-reference/keywords/null.md)，直到您使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子明確地建立類別的執行個體，或為它指派在他處建立的物件為止，如下列範例所示︰

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

建立物件時，會在 Managed 堆積上配置記憶體，而變數只會保留物件位置的參考。 配置以及由 CLR 的自動記憶體管理功能 (也就是「記憶體回收」) 回收 Managed 堆積上的類型時，都需要額外負荷。 不過，記憶體回收也已獲得高度最佳化，因此在大部分情況下並不會產生效能問題。 如需記憶體回收的詳細資訊，請參閱[自動記憶體管理和記憶體回收](../../../standard/garbage-collection/gc.md)。  
  
## <a name="declaring-classes"></a>宣告類別  
 使用 [class](../../../csharp/language-reference/keywords/class.md) 關鍵字宣告類別，如下列範例所示︰

 ```csharp
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` 關鍵字的前面會加上存取層級。 因為在此情況下會使用 [public](../../../csharp/language-reference/keywords/public.md)，所以所有人都可以從這個類別建立執行個體。 類別的名稱遵循 `class` 關鍵字。 定義的其餘部分是定義行為和資料的類別主體。 類別上的欄位、屬性、方法和事件統稱為「類別成員」。  
  
## <a name="creating-objects"></a>建立物件  
 雖然它們有時會交換使用，但是類別和物件不同。 類別會定義一種類型的物件，但不是物件本身。 物件是根據類別的具體實體，而且有時稱為類別的執行個體。  
  
 使用後面接著為物件基礎之類別名稱的 [new](../../../csharp/language-reference/keywords/new.md) 關鍵字，即可建立物件，與下面類似：  

 ```csharp
 Customer object1 = new Customer();
 ```
  
 建立類別的執行個體時，會將物件的參考傳回給程式設計人員。 在上述範例中，`object1` 是根據 `Customer` 之物件的參考。 這個參考參照新的物件，但不包含物件資料本身。 事實上，您可以建立物件參考，而根本不需要建立物件︰  
  
  ```csharp
  Customer object2;
  ```
  
 不建議建立物件參考，例如未參照物件的物件參考，因為在執行階段嘗試透過這類參考來存取物件將會失敗。 不過，可以進行這類參考來參照某個物件，方法是建立新的物件，或將它指派給現有物件，如下︰  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
 ```
  
 這個程式碼會建立同時參照相同物件的兩個物件參考。 因此，任何透過 `object3` 進行的物件變更都會反映在後續使用 `object4` 時。 因為以傳址方式參照根據類別的物件，所以類別稱為參考型別。  
  
## <a name="class-inheritance"></a>類別繼承  

 類別完全支援「繼承」，這是物件導向程式設計的基礎特性。 當您建立類別時，可以繼承自任何未定義為 [sealed](../../../csharp/language-reference/keywords/sealed.md) 的介面或類別，而其他類別可以繼承自您的類別並覆寫類別虛擬方法。

 使用「衍生」可完成繼承，這表示使用從中繼承資料和行為的「基底類別」來宣告類別。 附加冒號以及接著衍生類別名稱後面的基底類別名稱，以指定基底類別，與下面類似：  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 類別宣告基底類別時，會繼承基底類別的所有成員，但建構函式除外。 如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。
  
 與 C++ 不同，C# 中的類別只能直接繼承自一個基底類別。 不過，因為基底類別本身可以繼承自另一個類別，所以類別可能會間接繼承多個基底類別。 基至，類別可以直接實作多個介面。 如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
 類別可以宣告為 [abstract](../../../csharp/language-reference/keywords/abstract.md)。 抽象類別包含具有簽章定義但沒有實作的抽象方法。 無法具現化抽象類別。 它們僅用於實作抽象方法的衍生類別。 相較之下，[sealed](../../../csharp/language-reference/keywords/sealed.md) 類別不允許從它衍生其他類別。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
 類別定義可以在不同的原始程式檔之間進行分割。 如需詳細資訊，請參閱[部分類別和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## <a name="description"></a>描述  
 在下列範例中，定義包含單一欄位、方法以及稱為建構函式之特殊方法的公用類別。 如需詳細資訊，請參閱[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)。 然後使用 `new` 關鍵字具現化類別。  
  
## <a name="example"></a>範例  
 [!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [物件導向程式設計](../concepts/object-oriented-programming.md)  
 [多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [成員](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [物件](../../../csharp/programming-guide/classes-and-structs/objects.md)
