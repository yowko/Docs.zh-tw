---
title: "&lt;訊息&gt;此錯誤也可能是因為混用了檔案參考和組件 &#39; 的專案參考&lt;assemblyname&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fcbcc48928b1b03487f31930e3d14051ddd990a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="1924b-102">&lt;訊息&gt;此錯誤也可能是因為混用了檔案參考和組件 &#39; 的專案參考&lt;assemblyname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="1924b-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="1924b-103">\<訊息 > 這個錯誤也可能是因為混用了檔案參考和組件的專案參考 '\<assemblyname >。</span><span class="sxs-lookup"><span data-stu-id="1924b-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="1924b-104">在此情況下，請嘗試更換的檔案參考 '\<assemblyfilename >' 在專案'\<projectname1 >' 的專案參考 '\<專案名稱 2> >'。</span><span class="sxs-lookup"><span data-stu-id="1924b-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="1924b-105">您專案中的程式碼會存取另一個專案的成員，但您的解決方案組態不允許 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器解析參考。</span><span class="sxs-lookup"><span data-stu-id="1924b-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="1924b-106">若要存取另一個組件中所定義的類型， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器必須有該組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1924b-106">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="1924b-107">這必須是單一的明確參考，不會在專案之間造成循環參考。</span><span class="sxs-lookup"><span data-stu-id="1924b-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="1924b-108">**錯誤 ID︰** BC30971</span><span class="sxs-lookup"><span data-stu-id="1924b-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1924b-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1924b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="1924b-110">決定哪些專案產生的最佳組件供專案參考。</span><span class="sxs-lookup"><span data-stu-id="1924b-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="1924b-111">這項決策可能會使用輕鬆存取檔案和更新頻率等準則。</span><span class="sxs-lookup"><span data-stu-id="1924b-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="1924b-112">在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="1924b-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1924b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="1924b-113">See Also</span></span>  
 [<span data-ttu-id="1924b-114">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="1924b-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="1924b-115">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="1924b-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="1924b-116">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="1924b-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="1924b-117">針對中斷參考進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1924b-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
