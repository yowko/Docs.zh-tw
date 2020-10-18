---
title: <message> 此錯誤也可能是因為混用檔案參考與組件 '<assemblyname>' 的專案參考所致
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 9340c5c58c0cdb70c517534a339f57eb9ec1f906
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162423"
---
# <a name="bc30971-message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="a5c95-102">BC30971： \<message> 這個錯誤也可能是因為混用了檔案參考和元件 ' ' 的專案參考 \<assemblyname> 。</span><span class="sxs-lookup"><span data-stu-id="a5c95-102">BC30971: \<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>

<span data-ttu-id="a5c95-103">\<message> 這個錯誤也可能是因為混用了檔案參考和元件 ' 的專案參考 \<assemblyname> 。</span><span class="sxs-lookup"><span data-stu-id="a5c95-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="a5c95-104">在此情況下，請嘗試將專案 ' ' 中的 ' ' 檔案參考取代為 \<assemblyfilename> \<projectname1> ' ' 的專案參考 \<projectname2> 。</span><span class="sxs-lookup"><span data-stu-id="a5c95-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="a5c95-105">您專案中的程式碼會存取另一個專案的成員，但是解決方案的設定不允許 Visual Basic 編譯器解析參考。</span><span class="sxs-lookup"><span data-stu-id="a5c95-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>

 <span data-ttu-id="a5c95-106">若要存取在另一個元件中定義的類型，Visual Basic 編譯器必須有該元件的參考。</span><span class="sxs-lookup"><span data-stu-id="a5c95-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="a5c95-107">這必須是單一的明確參考，不會在專案之間造成循環參考。</span><span class="sxs-lookup"><span data-stu-id="a5c95-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>

 <span data-ttu-id="a5c95-108">**錯誤 ID︰** BC30971</span><span class="sxs-lookup"><span data-stu-id="a5c95-108">**Error ID:** BC30971</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a5c95-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a5c95-109">To correct this error</span></span>

1. <span data-ttu-id="a5c95-110">決定哪些專案產生的最佳組件供專案參考。</span><span class="sxs-lookup"><span data-stu-id="a5c95-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="a5c95-111">這項決策可能會使用輕鬆存取檔案和更新頻率等準則。</span><span class="sxs-lookup"><span data-stu-id="a5c95-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>

2. <span data-ttu-id="a5c95-112">在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="a5c95-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5c95-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5c95-113">See also</span></span>

- [<span data-ttu-id="a5c95-114">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="a5c95-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="a5c95-115">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="a5c95-115">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="a5c95-116">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="a5c95-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a5c95-117">針對中斷參考進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a5c95-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
