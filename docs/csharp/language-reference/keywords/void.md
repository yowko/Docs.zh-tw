---
title: "void (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
dev_langs:
- CSharp
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
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
ms.openlocfilehash: b4aa3c7c54e5e4d53975262adbbd9b54c701a69e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="void-c-reference"></a>void (C# 參考)
當 `void` 作為方法的傳回型別時，其可指定方法不要傳回值。  
  
 方法的參數清單中不允許 `void`。 如果某方法不採用任何參數，且不傳回任何值，其宣告方法如下所示：  
  
```  
public void SampleMethod()  
{  
    // Body of the method.  
}  
```  
  
 `void` 也可用於不安全的內容中，以宣告未知類型的指標。 如需詳細資訊，請參閱[指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)。  
  
 `void` 是 .NET Framework <xref:System.Void?displayProperty=fullName> 類型的別名。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [參考型別](../../../csharp/language-reference/keywords/reference-types.md)   
 [實值型別](../../../csharp/language-reference/keywords/value-types.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

