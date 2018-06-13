---
title: 如何：建立列舉類型的新方法 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 8de44cbddf26af45245709d0e28d2d157256ce59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313029"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="5ec56-102">如何：建立列舉類型的新方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5ec56-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="5ec56-103">您可以使用擴充方法來新增專屬於特定列舉類型的功能。</span><span class="sxs-lookup"><span data-stu-id="5ec56-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ec56-104">範例</span><span class="sxs-lookup"><span data-stu-id="5ec56-104">Example</span></span>  
 <span data-ttu-id="5ec56-105">在下例中，`Grades` 列舉代表班上學生可能得到的字母分級成績。</span><span class="sxs-lookup"><span data-stu-id="5ec56-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="5ec56-106">已將名為 `Passing` 的擴充方法新增至 `Grades` 類型，以便該類型的每個執行個體現在都「知道」它是否代表傳遞等級。</span><span class="sxs-lookup"><span data-stu-id="5ec56-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="5ec56-107">請注意，`Extensions` 類別也包含動態更新的靜態變數，以及反映該變數目前值的擴充方法傳回值。</span><span class="sxs-lookup"><span data-stu-id="5ec56-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="5ec56-108">本例示範，在幕後直接對定義所在的靜態類別叫用擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5ec56-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5ec56-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5ec56-109">Compiling the Code</span></span>  
 <span data-ttu-id="5ec56-110">若要執行此程式碼，請將它複製並貼到已在 Visual Studio 中建立的 Visual C# 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="5ec56-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="5ec56-111">根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="5ec56-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="5ec56-112">如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。</span><span class="sxs-lookup"><span data-stu-id="5ec56-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec56-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5ec56-113">See Also</span></span>  
 [<span data-ttu-id="5ec56-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5ec56-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5ec56-115">擴充方法</span><span class="sxs-lookup"><span data-stu-id="5ec56-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
