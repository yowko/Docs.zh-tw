---
title: 作法：顯示命令列引數 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: b7018afa1272f4ae092863de6b7f9ef783001244
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965588"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="abfa5-102">作法：顯示命令列引數 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="abfa5-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="abfa5-103">提供給命令列上可執行檔的引數，可以透過 `Main` 的選擇性參數來存取。</span><span class="sxs-lookup"><span data-stu-id="abfa5-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="abfa5-104">引數是以字串陣列的形式提供。</span><span class="sxs-lookup"><span data-stu-id="abfa5-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="abfa5-105">陣列的每個項目都包含一個引數。</span><span class="sxs-lookup"><span data-stu-id="abfa5-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="abfa5-106">引數之間的空白字元會被移除。</span><span class="sxs-lookup"><span data-stu-id="abfa5-106">White-space between arguments is removed.</span></span> <span data-ttu-id="abfa5-107">例如，請考慮這些虛擬可執行檔的命令列引動過程：</span><span class="sxs-lookup"><span data-stu-id="abfa5-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="abfa5-108">命令列上的輸入</span><span class="sxs-lookup"><span data-stu-id="abfa5-108">Input on Command-line</span></span>|<span data-ttu-id="abfa5-109">傳遞至 Main 的字串陣列</span><span class="sxs-lookup"><span data-stu-id="abfa5-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="abfa5-110">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="abfa5-110">**executable.exe a b c**</span></span>|<span data-ttu-id="abfa5-111">"a"</span><span class="sxs-lookup"><span data-stu-id="abfa5-111">"a"</span></span><br /><br /> <span data-ttu-id="abfa5-112">"b"</span><span class="sxs-lookup"><span data-stu-id="abfa5-112">"b"</span></span><br /><br /> <span data-ttu-id="abfa5-113">"c"</span><span class="sxs-lookup"><span data-stu-id="abfa5-113">"c"</span></span>|  
|<span data-ttu-id="abfa5-114">**executable.exe one two**</span><span class="sxs-lookup"><span data-stu-id="abfa5-114">**executable.exe one two**</span></span>|<span data-ttu-id="abfa5-115">"one"</span><span class="sxs-lookup"><span data-stu-id="abfa5-115">"one"</span></span><br /><br /> <span data-ttu-id="abfa5-116">"two"</span><span class="sxs-lookup"><span data-stu-id="abfa5-116">"two"</span></span>|  
|<span data-ttu-id="abfa5-117">**executable.exe "one two" three**</span><span class="sxs-lookup"><span data-stu-id="abfa5-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="abfa5-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="abfa5-118">"one two"</span></span><br /><br /> <span data-ttu-id="abfa5-119">"three"</span><span class="sxs-lookup"><span data-stu-id="abfa5-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="abfa5-120">在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。</span><span class="sxs-lookup"><span data-stu-id="abfa5-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abfa5-121">範例</span><span class="sxs-lookup"><span data-stu-id="abfa5-121">Example</span></span>  
 <span data-ttu-id="abfa5-122">此範例顯示傳遞至命令列應用程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="abfa5-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="abfa5-123">所顯示的輸出是上表中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="abfa5-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="abfa5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abfa5-124">See also</span></span>

- [<span data-ttu-id="abfa5-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="abfa5-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="abfa5-126">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="abfa5-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="abfa5-127">Main() 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="abfa5-127">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="abfa5-128">如何：使用 foreach 存取命令列引數</span><span class="sxs-lookup"><span data-stu-id="abfa5-128">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [<span data-ttu-id="abfa5-129">Main() 傳回值</span><span class="sxs-lookup"><span data-stu-id="abfa5-129">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
