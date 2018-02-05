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
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="bd243-102">如何：使用運算子多載建立複數類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bd243-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="bd243-103">此範例示範如何使用運算子多載來建立定義複數加法的 `Complex` 複數類別。</span><span class="sxs-lookup"><span data-stu-id="bd243-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="bd243-104">此程式會顯示數值的虛數和實數部分，以及使用 `ToString` 方法覆寫的加法結果。</span><span class="sxs-lookup"><span data-stu-id="bd243-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd243-105">範例</span><span class="sxs-lookup"><span data-stu-id="bd243-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bd243-106">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd243-106">See Also</span></span>  
 [<span data-ttu-id="bd243-107">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bd243-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bd243-108">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="bd243-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="bd243-109">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bd243-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 <span data-ttu-id="bd243-110">[Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/) (為什麼多載運算子在 C# 中一律為靜態？)</span><span class="sxs-lookup"><span data-stu-id="bd243-110">[Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)</span></span>
