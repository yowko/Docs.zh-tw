---
title: "如何：使用運算子多載建立複數類別 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e851b9d8a46f9cab73883a7b38761fed749c4f93
ms.sourcegitcommit: 22a48b64a0150a60b00b4fc4d8c62cde7f1670c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a>如何：使用運算子多載建立複數類別 (C# 程式設計手冊)
此範例示範如何使用運算子多載來建立定義複數加法的 `Complex` 複數類別。 此程式會顯示數值的虛數和實數部分，以及使用 `ToString` 方法覆寫的加法結果。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)  
 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)  
 [Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/) (為什麼多載運算子在 C# 中一律為靜態？)
