---
title: 如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 6ba6c6f50b4d2f717de4325b5cd21434066b2899
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43389180"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="e0f56-102">如何：在 LINQ 之外使用 Lambda 運算式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e0f56-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="e0f56-103">Lambda 運算式並不限於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="e0f56-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="e0f56-104">在預期會使用委派的任何位置，也就是任何可以使用匿名方法的位置，都可以使用這種運算式。</span><span class="sxs-lookup"><span data-stu-id="e0f56-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="e0f56-105">下列範例示範如何在 Windows Forms 事件處理常式中使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="e0f56-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="e0f56-106">請注意，輸入的類型 (<xref:System.Object> 和 <xref:System.Windows.Forms.MouseEventArgs>) 是由編譯器推斷，因此不需要在 Lambda 輸入參數中明確提供。</span><span class="sxs-lookup"><span data-stu-id="e0f56-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0f56-107">範例</span><span class="sxs-lookup"><span data-stu-id="e0f56-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0f56-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0f56-108">See Also</span></span>  
 [<span data-ttu-id="e0f56-109">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="e0f56-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="e0f56-110">匿名方法</span><span class="sxs-lookup"><span data-stu-id="e0f56-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="e0f56-111">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="e0f56-111">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
