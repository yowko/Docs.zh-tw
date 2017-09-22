---
title: "如何：使用 foreach 存取集合類別 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2ad81ab699b079f4aabb04a886211e94a937335d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：使用 foreach 存取集合類別 (C# 程式設計手冊)
下列程式碼範例說明如何撰寫可搭配 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 使用的非泛型集合類別。  此範例會定義從字串中取出語彙基元的類別。  
  
> [!NOTE]
>  此範例所呈現的建議作法，只適用於無法使用泛型集合類別的情況。  如需如何實作支援 <xref:System.Collections.Generic.IEnumerable%601> 之型別安全泛型集合類別的範例，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 在範例中，下列程式碼區段會使用 `Tokens` 類別將 "This is a sample sentence." 這個句子分成多個語彙基元 \(使用 ' ' 和 '\-' 做為分隔符號\)。  然後程式碼會使用 `foreach` 陳述式顯示這些語彙基元。  
  
 [!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a>範例  
 就內部而言，`Tokens` 類別會使用陣列來儲存權杖。 因為陣列實作 <xref:System.Collections.IEnumerator> 和 <xref:System.Collections.IEnumerable>，所以程式碼範例可能已用過陣列的列舉方法 (<xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A>)，而不是在 `Tokens` 類別中定義它們。 範例中所包含的方法定義是要釐清其定義方式和其用途。  
  
 [!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 在 C# 中，集合類別沒必要實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator>，以與 `foreach` 相容。 如果類別有所需的 <xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A> 和 <xref:System.Collections.IEnumerator.Current%2A> 成員，就能搭配 `foreach` 使用。 省略介面的優點是讓您定義 `Current` 的傳回型別，而這比 <xref:System.Object> 更為具體。 這提供類型安全。  
  
 例如，變更上述範例中的下列幾行。  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 由於 `Current` 傳回字串，因此當 `foreach` 陳述式中使用了不相容的型別時，編譯器便可偵測出來，如下列程式碼中所示。  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 省略 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator> 的缺點是集合類別無法再與其他 Common Language Runtime 語言的 `foreach` 陳述式或對等陳述式互通。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)

