---
title: "匿名方法 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
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
ms.openlocfilehash: 92842becf26a15ab1a6f5e9621002abf71dc67bc
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="anonymous-methods-c-programming-guide"></a>匿名方法 (C# 程式設計手冊)
在 C# 2.0 版之前，宣告[委派](../../../csharp/language-reference/keywords/delegate.md)的唯一方式是使用[具名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)。 C# 2.0 引入了匿名方法，而在 C# 3.0 和更新版本中，則是以 lambda 運算式取代匿名方法，成為撰寫程式碼內嵌的慣用方式。 不過，本主題中的匿名方法相關資訊也適用於 lambda 運算式。 有一種情況，是匿名方法提供了 lambda 運算式沒有的功能。 匿名方法能讓您省略參數清單。 這表示，匿名方法可以轉換成有各種不同簽章的委派。 這在 lambda 運算式是不可能的。 如需專門針對 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 建立匿名方法，其實是將程式碼區塊當成委派參數傳遞的方法。 以下是兩個範例：  
  
 [!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 使用匿名方法，您可以減少在具現化委派中撰寫程式碼的額外負荷，因為您不必另外建立一個方法。  
  
 例如，在必須建立某方法的情況下，而此方法可能不是那麼有必要的額外負荷時，指定程式碼區塊而不指定委派會很有用。 啟動新的執行緒時即是很好的範例。 這個類別會建立執行緒，而且也包含執行緒執行的程式碼，不需要為委派建立額外的方法。  
  
 [!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>備註  
 匿名方法的參數範圍是「匿名方法區塊」。  
  
 如果目標在區塊外，它是在匿名方法區塊內有跳躍陳述式的錯誤，例如 [goto](../../../csharp/language-reference/keywords/goto.md)、[break](../../../csharp/language-reference/keywords/break.md) 或 [continue](../../../csharp/language-reference/keywords/continue.md)。 如果目標在區塊內，它也是在匿名方法區塊外有跳躍陳述式的錯誤，例如 `goto`、`break` 或 `continue`。  
  
 範圍包含匿名方法宣告的本機變數和參數，稱為匿名方法的「外部」變數。 例如，在下列程式碼片段中，`n` 即為外部變數：  
  
 [!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 外部變數 `n` 的參考會在建立委派時「擷取」。 不同於本機變數，已擷取變數的存留期會延伸至參考匿名方法的委派符合記憶體回收資格。  
  
 匿名方法無法存取外部範圍的 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數。  
  
 無法存取「匿名方法區塊」內的任何不安全的程式碼。  
  
 匿名方法不可出現在 [is](../../../csharp/language-reference/keywords/is.md) 運算子的左邊。  
  
## <a name="example"></a>範例  
 下例示範兩種具現化委派的方式：  
  
-   建立委派與匿名方法的關聯。  
  
-   建立委派與具名方法 (`DoWork`) 的關聯。  
  
 在每個案例中，叫用委派時即會顯示訊息。  
  
 [!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [不安全的程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [具名方法委派與匿名方法委派](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)

