---
title: "類別 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "類別 [C#]"
  - "C# 語言，類別"
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 40
---
# 類別 (C# 程式設計手冊)
「*類別*」\(Class\) 是一種建構，可讓您建立自己的自訂協別，方法是將其他型別、方法和事件的變數群組在一起。  類別類似藍圖，  它定義型別的資料和行為。  如果類別未宣告為靜態 \(Static\)，用戶端程式碼可透過建立指派給變數的「*物件*」\(Object\) 或「*執行個體*」\(Instance\) 來使用該類別。  變數會一直保留在記憶體中，直到所有指向它的參考都離開範圍為止。  屆時，CLR 會將其標示為可以進行記憶體回收。  如果類別宣告為[靜態](../../../csharp/language-reference/keywords/static.md)，則記憶體中只會有一份複本，而用戶端程式碼只能透過類別本身存取該類別，不能透過「*執行個體變數*」\(Instance Variable\) 進行存取。  如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 與結構 \(Struct\) 不同的是，類別支援「*繼承*」\(Inheritance\)，而繼承是物件導向程式設計的基礎特性。  如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
## 宣告類別  
 類別是使用 [class](../../../csharp/language-reference/keywords/class.md) 關鍵字宣告的，如下列範例所示：  
  
 [!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 在 `class` 關鍵字之前是存取層級。  因為在此範例中使用 [public](../../../csharp/language-reference/keywords/public.md)，所以任何人都能從這個類別建立物件。  類別的名稱是跟隨在 `class` 關鍵字之後。  定義的其餘部分是類別主體，行為和資料就是在其中加以定義的。  類別上的欄位、屬性、方法和事件通稱為「*類別成員*」\(Class Member\)。  
  
## 建立物件  
 雖然類別和物件有時候會交替地使用，但這兩者並不相同。  類別會定義物件型別，但它不是物件本身。  物件是以類別為基礎的具象實體 \(Entity\)，而且有時候也稱為類別的執行個體 \(Instance\)。  
  
 使用 [new](../../../csharp/language-reference/keywords/new.md) 關鍵字，後面加上物件將會以其做為基礎之類別的名稱，即可建立物件，如下所示：  
  
 [!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 建立類別的執行個體後，物件的參考便會傳回給程式設計人員。  在上述範例中，`object1` 是以 `Customer` 為基礎之物件的參考。  這個參考會指向新的物件，但不會包含物件資料本身。  其實，您完全不用建立物件，就可以建立物件參考：  
  
 [!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 我們不建議您建立類似這種不參考物件的物件參考，因為在執行階段嘗試透過這樣的參考存取物件將會失敗。  然而，藉由建立新的物件，或是將參考指派到如下的現有物件，也可以讓這類參考指向物件：  
  
 [!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 此程式碼會建立參考同一物件的兩個物件參考。  因此，透過 `object3` 對物件所做的任何變更，將會反映在 `object4` 的後續使用中。  因為以類別為基礎的物件是以傳址 \(By Reference\) 方式進行參考，所以類別又稱為參考型別 \(Reference Type\)。  
  
## 類別繼承  
 繼承是使用「*衍生*」\(Derivation\) 來完成的，這表示類別是使用繼承資料和行為之來源的「*基底類別*」\(Base Class\) 所宣告的。  透過附加逗號和基底類別的名稱，然後再加上衍生的類別名稱，就可指定基底類別，如下所示：  
  
 [!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 當類別宣告基底類別時，它會繼承除了建構函式 \(Constructor\) 以外的所有基底類別成員。  
  
 與 C\+\+ 不同的是，C\# 中的類別只能從一個基底類別直接繼承。  不過，因為基底類別本身可能是繼承自另一個類別，所以一個類別可能間接繼承許多基底類別。  此外，類別可以直接實作一個以上的介面。  如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
 您可以將類別宣告為[抽象](../../../csharp/language-reference/keywords/abstract.md)。  抽象類別 \(Abstract Class\) 可以包含具有簽章定義但沒有實作 \(Implementation\) 的抽象方法。  抽象類別不能具現化 \(Instantiated\)，  只能透過實作抽象方法的衍生類別 \(Derived Class\) 來使用。  相較之下，[密封](../../../csharp/language-reference/keywords/sealed.md)類別不允許其他類別從它衍生。  如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
 類別定義可以分割，置於不同的原始程式檔中。  如需詳細資訊，請參閱[部分類別和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## 描述  
 在下列範例中，會定義一個公用類別，其中包含單一的欄位、一個方法，以及稱為建構函式 \(Constructor\) 的特殊方法。  如需詳細資訊，請參閱[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)。  接著，會以 `new` 關鍵字執行個體化類別。  
  
## 範例  
 [!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [物件導向程式設計](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)   
 [多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [成員](../../../csharp/programming-guide/classes-and-structs/members.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [物件](../../../csharp/programming-guide/classes-and-structs/objects.md)