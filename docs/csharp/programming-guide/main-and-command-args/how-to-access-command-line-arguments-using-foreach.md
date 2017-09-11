---
title: "如何：使用 foreach 存取命令列引數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
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
ms.openlocfilehash: 2f0e3bce88beafd45a21773a7b26ffb2bb41215d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="9351f-102">如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9351f-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="9351f-103">逐一查看陣列的另一種方法是使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式，如本例所示。</span><span class="sxs-lookup"><span data-stu-id="9351f-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="9351f-104">`foreach` 陳述式可用來逐一查看陣列、.NET Framework 集合類別，或實作 <xref:System.Collections.IEnumerable> 介面的任何類別或結構。</span><span class="sxs-lookup"><span data-stu-id="9351f-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9351f-105">在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](https://docs.microsoft.com/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。</span><span class="sxs-lookup"><span data-stu-id="9351f-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9351f-106">範例</span><span class="sxs-lookup"><span data-stu-id="9351f-106">Example</span></span>  
 <span data-ttu-id="9351f-107">本例會示範如何使用 `foreach` 印出命令列引數。</span><span class="sxs-lookup"><span data-stu-id="9351f-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 <span data-ttu-id="9351f-108">[!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9351f-108">[!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]</span></span>  
  
 <span data-ttu-id="9351f-109">[!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9351f-109">[!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9351f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9351f-110">See Also</span></span>  
 <span data-ttu-id="9351f-111"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="9351f-111"><xref:System.Array></span></span>   
 <span data-ttu-id="9351f-112"><xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="9351f-112"><xref:System.Collections></span></span>   
<span data-ttu-id="9351f-113"> [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span><span class="sxs-lookup"><span data-stu-id="9351f-113"> [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span></span>  
<span data-ttu-id="9351f-114"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9351f-114"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="9351f-115"> [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="9351f-115"> [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
<span data-ttu-id="9351f-116"> [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="9351f-116"> [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
<span data-ttu-id="9351f-117"> [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9351f-117"> [How to: Display Command Line Arguments](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md) </span></span>  
<span data-ttu-id="9351f-118"> [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)</span><span class="sxs-lookup"><span data-stu-id="9351f-118"> [Main() Return Values](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)</span></span>
