---
title: "類別 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eedb087f177b1bff6f4d4177cd56ac4cca016490
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="classes-c-programming-guide"></a>類別 (C# 程式設計手冊)
「類別」是一種建構，可讓您將其他類型、方法和事件的變數群組在一起，以建立您自己的自訂類型。 類別就像藍圖。 它會定義類型的資料和行為。 如果類別未宣告為 static，則用戶端程式碼可以使用它，方法是建立指派給變數的「物件」或「執行個體」。 除非變數的所有參考都超出範圍，否則變數會保留在記憶體中。 此時，CLR 會將它標記為適合進行記憶體回收。 如果類別宣告為 [static](../../../csharp/language-reference/keywords/static.md)，則記憶體中只會有一個複本，而且用戶端程式碼只能透過類別本身存取它，而非「執行個體變數」。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 與結構不同，類別支援「繼承」，這是物件導向程式設計的基礎特性。 如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
## <a name="declaring-classes"></a>宣告類別  
 使用 [class](../../../csharp/language-reference/keywords/class.md) 關鍵字宣告類別，如下列範例所示︰  
  
 [!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 `class` 關鍵字的前面會加上存取層級。 因為在此情況下使用 [public](../../../csharp/language-reference/keywords/public.md)，所以所有人都可以從這個類別建立物件。 類別的名稱遵循 `class` 關鍵字。 定義的其餘部分是定義行為和資料的類別主體。 類別上的欄位、屬性、方法和事件統稱為「類別成員」。  
  
## <a name="creating-objects"></a>建立物件  
 雖然它們有時會交換使用，但是類別和物件不同。 類別會定義一種類型的物件，但不是物件本身。 物件是根據類別的具體實體，而且有時稱為類別的執行個體。  
  
 使用後面接著為物件基礎之類別名稱的 [new](../../../csharp/language-reference/keywords/new.md) 關鍵字，即可建立物件，與下面類似：  
  
 [!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 建立類別的執行個體時，會將物件的參考傳回給程式設計人員。 在上述範例中，`object1` 是根據 `Customer` 之物件的參考。 這個參考參照新的物件，但不包含物件資料本身。 事實上，您可以建立物件參考，而根本不需要建立物件︰  
  
 [!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 不建議建立物件參考，例如未參照物件的物件參考，因為在執行階段嘗試透過這類參考來存取物件將會失敗。 不過，可以進行這類參考來參照某個物件，方法是建立新的物件，或將它指派給現有物件，如下︰  
  
 [!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 這個程式碼會建立同時參照相同物件的兩個物件參考。 因此，任何透過 `object3` 進行的物件變更都會反映在後續使用 `object4` 時。 因為以傳址方式參照根據類別的物件，所以類別稱為參考型別。  
  
## <a name="class-inheritance"></a>類別繼承  
 使用「衍生」可完成繼承，這表示使用從中繼承資料和行為的「基底類別」來宣告類別。 附加冒號以及接著衍生類別名稱後面的基底類別名稱，以指定基底類別，與下面類似：  
  
 [!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 類別宣告基底類別時，會繼承基底類別的所有成員，但建構函式除外。  
  
 與 C++ 不同，C# 中的類別只能直接繼承自一個基底類別。 不過，因為基底類別本身可以繼承自另一個類別，所以類別可能會間接繼承多個基底類別。 基至，類別可以直接實作多個介面。 如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
 類別可以宣告為 [abstract](../../../csharp/language-reference/keywords/abstract.md)。 抽象類別包含具有簽章定義但沒有實作的抽象方法。 無法具現化抽象類別。 它們僅用於實作抽象方法的衍生類別。 相較之下，[sealed](../../../csharp/language-reference/keywords/sealed.md) 類別不允許從它衍生其他類別。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
 類別定義可以在不同的原始程式檔之間進行分割。 如需詳細資訊，請參閱[部分類別和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## <a name="description"></a>描述  
 在下列範例中，定義包含單一欄位、方法以及稱為建構函式之特殊方法的公用類別。 如需詳細資訊，請參閱[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)。 然後使用 `new` 關鍵字具現化類別。  
  
## <a name="example"></a>範例  
 [!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [物件導向程式設計](../concepts/object-oriented-programming.md)   
 [多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [成員](../../../csharp/programming-guide/classes-and-structs/members.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [物件](../../../csharp/programming-guide/classes-and-structs/objects.md)

