---
title: "return (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
dev_langs:
- CSharp
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
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
ms.openlocfilehash: ce15455381a3279a8c77eaa1fb25494cfe5dfc2b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="return-c-reference"></a>return (C# 參考)
`return` 陳述式會終止執行在其中出現的方法，並且將控制權傳回給呼叫方法。 它也可以傳回選擇性值。 如果方法是 `void` 類型，則可以省略 `return` 陳述式。  
  
 如果 return 陳述式位在 `try` 區塊內，則會先執行 `finally` 區塊 (如果存在的話)，控制權才會傳回到呼叫方法。  
  
## <a name="example"></a>範例  
 在下列範例中，`A()` 方法會將變數 `Area` 傳回為 [double](../../../csharp/language-reference/keywords/double.md) 值。  
  
 [!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [return 陳述式](https://docs.microsoft.com/cpp/cpp/return-statement-cpp)   
 [跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)
