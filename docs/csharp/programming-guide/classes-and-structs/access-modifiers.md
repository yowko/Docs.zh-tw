---
title: "存取修飾詞 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "存取修飾詞 [C#], 關於"
  - "C# 語言, 存取修飾詞"
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 32
---
# 存取修飾詞 (C# 程式設計手冊)
所有型別與型別成員都有存取層級，用來控制您的組件或其他組建中的其他程式碼是否可以使用這些型別與成員。  您可以在宣告型別或成員時，使用下列存取修飾詞指定存取範圍：  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 型別或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。  
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 型別或成員只能由相同類別或結構中的程式碼存取。  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 型別或成員只能由相同類別或結構，或是在衍生自該類別的類別中存取。  
  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 型別或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。  
  
 `protected internal`  
 型別或成員可由其宣告所在組件中的任何程式碼，或是從其他組件的衍生類別中存取。  從另一個組譯碼存取，必須發生在類別宣告中，此宣告必須衍生自宣告受保護內部項目的類別，且必須透過衍生類別類型的執行個體發生。  
  
 以下範例示範如何指定型別和成員上的存取修飾詞：  
  
 [!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/access-modifiers_1.cs)]  
  
 並非所有存取修飾詞在任何情況下都可供所有型別或成員使用，而且在某些情況下，型別成員的存取範圍會受到其包含型別的存取範圍限制。  以下章節提供更多關於存取範圍的詳細資訊。  
  
## 類別和結構的存取範圍  
 直接在命名空間中宣告的類別和結構 \(換句話說，並未在其他類別或結構中巢狀化\) 可以是 public 或 internal。  如果未指定存取修飾詞，則預設值為 internal。  
  
 結構成員，包括巢狀類別和結構，可宣告為公用、內部，或私用。  類別成員 \(包括巢狀類別和結構\) 可以是 public、protected internal、protected、internal 或 private。  預設情況下，類別成員和結構成員 \(包括巢狀類別和結構\) 的存取級別是私用的。  私用巢狀型別無法從包含型別的外部存取。  
  
 衍生類別的存取範圍不可大於其基底型別的存取範圍。  換句話說，不可以有衍生自 internal 類別 `A` 的 public 類別 `B`。  如果允許這種情況出現，則 `A` 會變成 public，因為 `A` 的所有 protected 或 internal 成員都可從衍生類別存取。  
  
 您可以使用 InternalsVisibleToAttribute 讓其他特定組件存取您的 internal 型別。  如需詳細資訊，請參閱 [Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 類別和結構成員的存取範圍  
 類別成員 \(包括巢狀類別和結構\) 可使用五種存取型別的任一種宣告。  結構成員無法宣告為 protected，因為結構不支援繼承。  
  
 通常，成員的存取範圍不會大於包含該成員之型別的存取範圍。  但是，如果成員實作介面方法或覆寫在公用基底類別中定義的虛擬方法，則可能可以從組件外部存取內部類別的公用成員。  
  
 本身為欄位、屬性或事件之任何成員的型別必須至少與該成員一樣可供存取。  同樣地，任何為方法、索引子或委派的任何成員之傳回型別和參數型別至少必須和成員本身一樣可以存取。  例如，不可以有傳回類別 `C` 的 public 方法 `M`，除非 `C` 同樣是 public。  同樣地，如果 `A` 宣告為 private，則型別 `A` 不可以有 protected 屬性。  
  
 使用者定義的運算子必須永遠宣告為 public。  如需詳細資訊，請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)。  
  
 解構函式不能有存取範圍修飾詞。  
  
 若要設定類別或結構成員的存取層級，請將適當的關鍵字加入至成員宣告中，如下列範例中所示。  
  
 [!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  protected internal 存取範圍層級的意義是 protected 或 internal，而不是 protected 且 internal。  換句話說，可以從相同組件中的任何類別存取受保護的內部成員，包括衍生類別。  若要將存取範圍限制為僅在相同組件中的衍生類別，請將類別本身宣告為 internal，並且將其成員宣告為 protected。  
  
## 其他型別  
 直接在命名空間內宣告的介面可以宣告為公用或內部，而且就像類別和結構，介面會預設為內部存取。  介面成員固定為 public，因為介面的目的在於讓其他型別存取類別或結構。  介面成員無法套用任何存取修飾詞。  
  
 列舉型別成員也都是公用成員，無法套用任何存取修飾詞。  
  
 類別和建構之類的委派行為。  根據預設，這些成員直接宣告於命名空間中時會有內部存取權，而在巢狀化時則有私用存取權。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [Class \- 類別](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)