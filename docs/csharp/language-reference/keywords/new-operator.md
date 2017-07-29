---
title: "new 運算子 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f0831bbbaf68c8c9e1e0e2d77ccf18e7c8b42e4a
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="new-operator-c-reference"></a>new 運算子 (C# 參考)
用以建立物件及叫用建構函式。 例如：  
  
```  
Class1 obj  = new Class1();  
```  
  
 它也用來建立匿名型別的執行個體︰  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 `new` 運算子也可以用來叫用實值型別的預設建構函式。 例如：  
  
```  
int i = new int();  
```  
  
 在前一個陳述式中，`i` 會初始化為 `0`，這是 `int` 型別的預設值。 此陳述式與下例效果相同：  
  
```  
int i = 0;  
```  
  
 如需預設值的完整清單，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  
  
 請記住，為 [struct](../../../csharp/language-reference/keywords/struct.md) 宣告預設建構函式是錯誤，因為每一個實值型別都有隱含的公用預設建構函式。 在結構型別上宣告參數化建構函式以設定其初始值是可能的，但只有需要預設值以外的值時才為必要。  
  
 結構等實值型別物件是建立在堆疊上，而類別等參考型別物件則是建立在堆積上。 這兩種物件型別都會自動終結，但實值型別物件是在超出範圍時終結，而參考型別物件則是在移除其最後一個參考後的未指定時間終結。 對於使用大量記憶體、檔案控制代碼或網路連線等固定資源的參考類型而言，有時候非常需要採用具決定性的最終處理，以確保儘速終結物件。 如需詳細資訊，請參閱[使用陳述式](../../../csharp/language-reference/keywords/using-statement.md)。  
  
 `new` 運算子無法多載。  
  
 如果 `new` 運算子無法配置記憶體，則會擲回例外狀況 <xref:System.OutOfMemoryException>。  
  
## <a name="example"></a>範例  
 下例使用 `new` 運算子建立並初始化 `struct` 物件和類別物件，然後為物件指派值。 顯示預設值和指派的值。  
  
 [!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 請注意，範例中的字串預設值是 `null`。 因此，不會顯示。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
