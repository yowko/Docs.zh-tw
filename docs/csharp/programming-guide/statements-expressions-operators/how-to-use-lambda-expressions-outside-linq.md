---
title: "如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 12
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
ms.openlocfilehash: 54e1c54c0fe06847a5d36ca1e58b21884880bc3c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="3d3cf-102">如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3d3cf-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="3d3cf-103">Lambda 運算式並不限於 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="3d3cf-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] queries.</span></span> <span data-ttu-id="3d3cf-104">在預期會使用委派的任何位置，也就是任何可以使用匿名方法的位置，都可以使用這種運算式。</span><span class="sxs-lookup"><span data-stu-id="3d3cf-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="3d3cf-105">下列範例示範如何在 Windows Forms 事件處理常式中使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="3d3cf-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="3d3cf-106">請注意，輸入的類型 (<xref:System.Object> 和 <xref:System.Windows.Forms.MouseEventArgs>) 是由編譯器推斷，因此不需要在 Lambda 輸入參數中明確提供。</span><span class="sxs-lookup"><span data-stu-id="3d3cf-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d3cf-107">範例</span><span class="sxs-lookup"><span data-stu-id="3d3cf-107">Example</span></span>  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d3cf-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d3cf-108">See Also</span></span>  
 <span data-ttu-id="3d3cf-109">[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="3d3cf-109">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="3d3cf-110"> [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="3d3cf-110"> [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
<span data-ttu-id="3d3cf-111"> [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)</span><span class="sxs-lookup"><span data-stu-id="3d3cf-111"> [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)</span></span>
