---
title: "如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="905df-102">如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="905df-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="905df-103">逐一查看陣列的另一種方法是使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式，如本例所示。</span><span class="sxs-lookup"><span data-stu-id="905df-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="905df-104">`foreach` 陳述式可用來逐一查看陣列、.NET Framework 集合類別，或實作 <xref:System.Collections.IEnumerable> 介面的任何類別或結構。</span><span class="sxs-lookup"><span data-stu-id="905df-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="905df-105">在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁面](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。</span><span class="sxs-lookup"><span data-stu-id="905df-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="905df-106">範例</span><span class="sxs-lookup"><span data-stu-id="905df-106">Example</span></span>  
 <span data-ttu-id="905df-107">本例會示範如何使用 `foreach` 印出命令列引數。</span><span class="sxs-lookup"><span data-stu-id="905df-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="905df-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="905df-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="905df-109">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="905df-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="905df-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="905df-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="905df-111">foreach、in</span><span class="sxs-lookup"><span data-stu-id="905df-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="905df-112">Main() 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="905df-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="905df-113">如何：顯示命令列引數</span><span class="sxs-lookup"><span data-stu-id="905df-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="905df-114">Main() 傳回值</span><span class="sxs-lookup"><span data-stu-id="905df-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
