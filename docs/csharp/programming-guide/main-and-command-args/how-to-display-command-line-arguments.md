---
title: '如何顯示命令列引數-c # 程式設計指南'
description: 瞭解如何顯示命令列引數。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 717e27c23724e63c03a38b028ef99dc6530b4745
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195476"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="c0fde-104">如何顯示命令列引數 (c # 程式設計指南) </span><span class="sxs-lookup"><span data-stu-id="c0fde-104">How to display command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="c0fde-105">在命令列上提供給可執行檔的引數可透過的選擇性參數來存取 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="c0fde-105">Arguments provided to an executable on the command line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="c0fde-106">引數是以字串陣列的形式提供。</span><span class="sxs-lookup"><span data-stu-id="c0fde-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="c0fde-107">陣列的每個項目都包含一個引數。</span><span class="sxs-lookup"><span data-stu-id="c0fde-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="c0fde-108">引數之間的空白字元會被移除。</span><span class="sxs-lookup"><span data-stu-id="c0fde-108">White-space between arguments is removed.</span></span> <span data-ttu-id="c0fde-109">例如，請考慮這些虛擬可執行檔的命令列引動過程：</span><span class="sxs-lookup"><span data-stu-id="c0fde-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="c0fde-110">命令列上的輸入</span><span class="sxs-lookup"><span data-stu-id="c0fde-110">Input on command line</span></span>|<span data-ttu-id="c0fde-111">傳遞至 Main 的字串陣列</span><span class="sxs-lookup"><span data-stu-id="c0fde-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="c0fde-112">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="c0fde-112">**executable.exe a b c**</span></span>|<span data-ttu-id="c0fde-113">"a"</span><span class="sxs-lookup"><span data-stu-id="c0fde-113">"a"</span></span><br /><br /> <span data-ttu-id="c0fde-114">"b"</span><span class="sxs-lookup"><span data-stu-id="c0fde-114">"b"</span></span><br /><br /> <span data-ttu-id="c0fde-115">"c"</span><span class="sxs-lookup"><span data-stu-id="c0fde-115">"c"</span></span>|  
|<span data-ttu-id="c0fde-116">**executable.exe one two**</span><span class="sxs-lookup"><span data-stu-id="c0fde-116">**executable.exe one two**</span></span>|<span data-ttu-id="c0fde-117">"one"</span><span class="sxs-lookup"><span data-stu-id="c0fde-117">"one"</span></span><br /><br /> <span data-ttu-id="c0fde-118">"two"</span><span class="sxs-lookup"><span data-stu-id="c0fde-118">"two"</span></span>|  
|<span data-ttu-id="c0fde-119">**executable.exe "one two" three**</span><span class="sxs-lookup"><span data-stu-id="c0fde-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="c0fde-120">"one two"</span><span class="sxs-lookup"><span data-stu-id="c0fde-120">"one two"</span></span><br /><br /> <span data-ttu-id="c0fde-121">"three"</span><span class="sxs-lookup"><span data-stu-id="c0fde-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c0fde-122">在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。</span><span class="sxs-lookup"><span data-stu-id="c0fde-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0fde-123">範例</span><span class="sxs-lookup"><span data-stu-id="c0fde-123">Example</span></span>  

 <span data-ttu-id="c0fde-124">此範例會顯示傳遞至命令列應用程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="c0fde-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="c0fde-125">所顯示的輸出是上表中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="c0fde-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c0fde-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0fde-126">See also</span></span>

- [<span data-ttu-id="c0fde-127">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c0fde-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c0fde-128">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="c0fde-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="c0fde-129">主要 ( # A1 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="c0fde-129">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="c0fde-130">Main() 傳回值</span><span class="sxs-lookup"><span data-stu-id="c0fde-130">Main() Return Values</span></span>](./main-return-values.md)
