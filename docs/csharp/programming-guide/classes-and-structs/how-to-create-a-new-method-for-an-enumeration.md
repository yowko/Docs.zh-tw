---
title: '如何建立列舉的新方法-c # 程式設計手冊'
description: '瞭解如何使用擴充方法，將功能新增至 c # 中的列舉。 這個範例會顯示一個稱為「成績等級」的擴充方法，其會傳遞給列舉。'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 6c01a73476e98e8344a7a8dc35a5fd80384fc7a2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864484"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="9e0eb-104">如何建立列舉的新方法（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="9e0eb-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="9e0eb-105">您可以使用擴充方法來新增專屬於特定列舉類型的功能。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e0eb-106">範例</span><span class="sxs-lookup"><span data-stu-id="9e0eb-106">Example</span></span>  
 <span data-ttu-id="9e0eb-107">在下例中，`Grades` 列舉代表班上學生可能得到的字母分級成績。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="9e0eb-108">已將名為 `Passing` 的擴充方法新增至 `Grades` 類型，以便該類型的每個執行個體現在都「知道」它是否代表傳遞等級。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="9e0eb-109">請注意，`Extensions` 類別也包含動態更新的靜態變數，以及反映該變數目前值的擴充方法傳回值。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="9e0eb-110">本例示範，在幕後直接對定義所在的靜態類別叫用擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0eb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e0eb-111">See also</span></span>

- [<span data-ttu-id="9e0eb-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9e0eb-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9e0eb-113">擴充方法</span><span class="sxs-lookup"><span data-stu-id="9e0eb-113">Extension Methods</span></span>](./extension-methods.md)
