---
title: "類型參數的條件約束 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "泛型 [C#], 類型條件約束"
  - "類型條件約束 [C#]"
  - "類型參數 [C#], 條件約束"
  - "未繫結類型參數 [C#]"
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 41
---
# 類型參數的條件約束 (C# 程式設計手冊)
當您定義泛型類別時，可限制用戶端程式碼在執行個體化類別時，型別引數可以使用哪些型別。  如果用戶端程式碼嘗試使用條件約束所不允許的型別來執行個體化類別，就會產生編譯時期錯誤。  這些限制稱為條件約束。  您可以使用 `where` 內容關鍵字指定條件約束。  下表列出六種條件約束：  
  
|條件約束|描述|  
|----------|--------|  
|where T: struct|型別引數必須是實值型別。  您可以指定 <xref:System.Nullable> 以外的任何實值型別。  如需詳細資訊，請參閱 [用可為 Null 的類型](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)。|  
|where T : class|型別引數必須是參考型別，這是指任何類別、介面、委派或陣列型別。|  
|where T : new\(\)|型別引數必須擁有公用的無參數建構函式。  將 `new()` 條件約束與其他條件約束一起使用時，一定要將其指定為最後一個。|  
|where T : \<base class name\>|型別引數必須本身是指定的基底類別，或衍生自該類別。|  
|where T : \<interface name\>|型別引數必須本身是指定的介面，或實作該介面。  您可以同時指定多個介面條件約束。  限制的介面也可以是泛型的。|  
|where T : U|提供給 T 的型別引數必須是 \(或衍生自\) 提供給 U 的引數。|  
  
## 使用條件約束的原因  
 如果您要檢查泛型清單中的某個項目，判斷是否有效或是要與其他項目比較，編譯器就必須確定需要呼叫的運算子或方法，能夠受到用戶端程式碼可能指定之任何型別引數的支援。  因此，只有將一或多個條件約束套用至泛型類別定義，才能確保支援。  例如，基底類別條件約束可讓編譯器知道，只有這種型別的物件或衍生自該型別的物件才可以當做型別引數使用。  只要編譯器確定能夠獲得這項支援，便可允許在泛型類別中呼叫該型別的方法。  您可以使用內容關鍵字 `where` 套用條件約束。  下列程式碼範例示範如何套用基底類別條件約束，以將功能加入至 `GenericList<T>` 類別 \(在[泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md) 中\)。  
  
 [!code-cs[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/csharp/constraints-on-type-para_1.cs)]  
  
 該條件約束可讓泛型類別使用 `Employee.Name` 屬性，因為型別 T 的所有項目都一定會是 `Employee` 物件，或繼承自 `Employee` 的物件。  
  
 同一型別參數可套用多個條件約束，而且條件約束本身可以是泛型型別，如下所示：  
  
 [!code-cs[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/csharp/constraints-on-type-para_2.cs)]  
  
 藉由限制型別參數，您便可以增加允許的運算和方法呼叫數目，只要使用條件約束型別和其繼承階層架構內的所有型別，運算和方法呼叫都會受到支援。  因此，在設計泛型類別或方法時，如果在泛型成員上所執行的運算不單只是設定，或是要呼叫 `System.Object` 不支援的任何方法，就需要對型別參數套用條件約束。  
  
 套用 `where T : class` 條件約束時，請避免在型別參數上使用 `==` 和 `!=` 運算子，因為這些運算子只會測試參考識別，而不會測試值相等與否。  即使這些運算子在當做引數使用的型別中多載，情況也會是一樣。  下列程式碼便說明這點，雖然 <xref:System.String> 類別多載 `==` 運算子，但輸出仍會是 false。  
  
 [!code-cs[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/csharp/constraints-on-type-para_3.cs)]  
  
 這是因為在編譯時期，編譯器只知道 T 是參考型別，因此必須使用對所有參考型別都有效的預設運算子。  如果必須測試值是否相等，建議您同時套用 `where T : IComparable<T>` 條件約束，然後在用來建構該泛型類別的任何類別中實作該介面即可。  
  
## 限制多個參數  
 您可以將多個條件約束套用至多個參數，也可以將多個條件約束套用至單一參數，如以下範例所示：  
  
 [!code-cs[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/csharp/constraints-on-type-para_4.cs)]  
  
## 未繫結的型別參數  
 沒有條件約束的型別參數 \(例如公用類別 `SampleClass<T>{}` 中的 T\) 稱為未繫結的型別參數。  未繫結的型別參數有下列規則：  
  
-   無法使用 `!=` 和 `==` 運算子，因為不能確定實體的型別引數是否會支援這些運算子。  
  
-   這些參數可與 `System.Object` 相互轉換或明確轉換成任何介面型別。  
  
-   您可以與 [null](../../../csharp/language-reference/keywords/null.md) 比較。  如果將未繫結的型別參數與 `null` 比較，那麼當型別引數為實值型別時，一定會傳回 false。  
  
## 做為條件約束的型別參數  
 當成員函式本身的型別參數需要限制為包含型別的型別參數時，使用泛型型別參數做為條件約束就很有用，如下列範例所示：  
  
 [!code-cs[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/csharp/constraints-on-type-para_5.cs)]  
  
 在上面的程式碼範例中，`T` 在 `Add` 方法的內容中是型別條件約束，而在 `List` 類別的內容中則是未繫結的型別參數。  
  
 型別參數也可以當做泛型類別定義中的條件約束使用。  請注意，型別參數必須與其他型別參數一起在角括弧中宣告：  
  
 [!code-cs[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/csharp/constraints-on-type-para_6.cs)]  
  
 做為條件約束的型別參數對泛型類別來說不會很有用，因為編譯器除了只能將型別參數視為是衍生自 `System.Object` 之外，無法做任何假設。  如果您要強制兩型別參數之間的繼承關係時，請在泛型類別上使用型別參數條件約束。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)   
 [new 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)