---
title: "如何：顯示命令列引數 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
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
ms.openlocfilehash: cf8a57cce252b3596f0a19c9df643427615467c6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="4d02d-102">如何：顯示命令列引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4d02d-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="4d02d-103">提供給命令列上可執行檔的引數，可以透過 `Main` 的選擇性參數來存取。</span><span class="sxs-lookup"><span data-stu-id="4d02d-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="4d02d-104">引數是以字串陣列的形式提供。</span><span class="sxs-lookup"><span data-stu-id="4d02d-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="4d02d-105">陣列的每個項目都包含一個引數。</span><span class="sxs-lookup"><span data-stu-id="4d02d-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="4d02d-106">引數之間的空白字元會被移除。</span><span class="sxs-lookup"><span data-stu-id="4d02d-106">White-space between arguments is removed.</span></span> <span data-ttu-id="4d02d-107">例如，請考慮這些虛擬可執行檔的命令列引動過程：</span><span class="sxs-lookup"><span data-stu-id="4d02d-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="4d02d-108">命令列上的輸入</span><span class="sxs-lookup"><span data-stu-id="4d02d-108">Input on Command-line</span></span>|<span data-ttu-id="4d02d-109">傳遞至 Main 的字串陣列</span><span class="sxs-lookup"><span data-stu-id="4d02d-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="4d02d-110">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="4d02d-110">**executable.exe a b c**</span></span>|<span data-ttu-id="4d02d-111">"a"</span><span class="sxs-lookup"><span data-stu-id="4d02d-111">"a"</span></span><br /><br /> <span data-ttu-id="4d02d-112">"b"</span><span class="sxs-lookup"><span data-stu-id="4d02d-112">"b"</span></span><br /><br /> <span data-ttu-id="4d02d-113">"c"</span><span class="sxs-lookup"><span data-stu-id="4d02d-113">"c"</span></span>|  
|<span data-ttu-id="4d02d-114">**executable.exe one two**</span><span class="sxs-lookup"><span data-stu-id="4d02d-114">**executable.exe one two**</span></span>|<span data-ttu-id="4d02d-115">"one"</span><span class="sxs-lookup"><span data-stu-id="4d02d-115">"one"</span></span><br /><br /> <span data-ttu-id="4d02d-116">"two"</span><span class="sxs-lookup"><span data-stu-id="4d02d-116">"two"</span></span>|  
|<span data-ttu-id="4d02d-117">**executable.exe "one two" three**</span><span class="sxs-lookup"><span data-stu-id="4d02d-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="4d02d-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="4d02d-118">"one two"</span></span><br /><br /> <span data-ttu-id="4d02d-119">"three"</span><span class="sxs-lookup"><span data-stu-id="4d02d-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4d02d-120">在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。</span><span class="sxs-lookup"><span data-stu-id="4d02d-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d02d-121">範例</span><span class="sxs-lookup"><span data-stu-id="4d02d-121">Example</span></span>  
 <span data-ttu-id="4d02d-122">此範例顯示傳遞至命令列應用程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="4d02d-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="4d02d-123">所顯示的輸出是上表中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="4d02d-123">The output shown is for the first entry in the table above.</span></span>  
  
 <span data-ttu-id="4d02d-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4d02d-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d02d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d02d-125">See Also</span></span>  
 <span data-ttu-id="4d02d-126">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d02d-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4d02d-127">[使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span><span class="sxs-lookup"><span data-stu-id="4d02d-127">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span></span>  
 <span data-ttu-id="4d02d-128">[Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d02d-128">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 <span data-ttu-id="4d02d-129">[如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span><span class="sxs-lookup"><span data-stu-id="4d02d-129">[How to: Access Command-Line Arguments Using foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span></span>  
 [<span data-ttu-id="4d02d-130">Main() 傳回值</span><span class="sxs-lookup"><span data-stu-id="4d02d-130">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

