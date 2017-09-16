---
title: "泛型委派 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
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
ms.openlocfilehash: be067e2a2e2a192da8ccc92b60af81f0999c449a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="generic-delegates-c-programming-guide"></a>泛型委派 (C# 程式設計手冊)
[委派](../../../csharp/language-reference/keywords/delegate.md)可以定義自己的型別參數。 參考泛型委派的程式碼，可以指定型別引數建立封閉式建構類型，就像在具現化泛型類別或呼叫泛型方法時一樣，如下列範例所示：  
  
 [!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C# 2.0 版具有方法群組轉換新功能，適用於實體及泛型委派類型，並可讓您使用這個簡化的語法撰寫上一行：  
  
 [!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 在泛型類別中定義的委派，可以使用和類別方法相同的方式，使用泛型類別類型參數。  
  
 [!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 參考委派的程式碼必須指定包含類別的型別引數，如下所示：  
  
 [!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 泛型委派在根據一般設計模式定義事件方面特別有幫助，因為傳送者引數可以是強型別，不必再在 <xref:System.Object> 間來回轉換。  
  
 [!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [泛型方法](../../../csharp/programming-guide/generics/generic-methods.md)   
 [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)   
 [泛型介面](../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [泛型](~/docs/standard/generics/index.md)

