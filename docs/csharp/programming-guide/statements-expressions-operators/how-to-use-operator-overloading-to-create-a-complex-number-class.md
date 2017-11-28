---
title: "如何：使用運算子多載建立複數類別 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2053684a9b20c3ec8f4d8ac275832516b3f2c265
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="6bbfa-102">如何：使用運算子多載建立複數類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6bbfa-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="6bbfa-103">此範例示範如何使用運算子多載來建立定義複數加法的 `Complex` 複數類別。</span><span class="sxs-lookup"><span data-stu-id="6bbfa-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="6bbfa-104">此程式會顯示數值的虛數和實數部分，以及使用 `ToString` 方法覆寫的加法結果。</span><span class="sxs-lookup"><span data-stu-id="6bbfa-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bbfa-105">範例</span><span class="sxs-lookup"><span data-stu-id="6bbfa-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6bbfa-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bbfa-106">See Also</span></span>  
 [<span data-ttu-id="6bbfa-107">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6bbfa-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6bbfa-108">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6bbfa-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="6bbfa-109">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6bbfa-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 <span data-ttu-id="6bbfa-110">[Why are overloaded operators always static in C#?](http://go.microsoft.com/fwlink/?LinkId=112383) (為什麼多載運算子在 C# 中一律為靜態？)</span><span class="sxs-lookup"><span data-stu-id="6bbfa-110">[Why are overloaded operators always static in C#?](http://go.microsoft.com/fwlink/?LinkId=112383)</span></span>
