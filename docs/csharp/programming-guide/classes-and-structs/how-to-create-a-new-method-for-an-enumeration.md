---
title: '如何建立列舉的新方法-c # 程式設計指南'
description: '瞭解如何使用擴充方法，以 c # 將功能加入至列舉。 這個範例會示範一個稱為「成績」之列舉傳遞的擴充方法。'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 88afff854b8136bde837db8effb0e0eb512e1099
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513090"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="b1ac6-104">如何建立列舉的新方法 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="b1ac6-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>

<span data-ttu-id="b1ac6-105">您可以使用擴充方法來新增專屬於特定列舉類型的功能。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ac6-106">範例</span><span class="sxs-lookup"><span data-stu-id="b1ac6-106">Example</span></span>  

 <span data-ttu-id="b1ac6-107">在下例中，`Grades` 列舉代表班上學生可能得到的字母分級成績。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="b1ac6-108">已將名為 `Passing` 的擴充方法新增至 `Grades` 類型，以便該類型的每個執行個體現在都「知道」它是否代表傳遞等級。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="b1ac6-109">請注意，`Extensions` 類別也包含動態更新的靜態變數，以及反映該變數目前值的擴充方法傳回值。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="b1ac6-110">本例示範，在幕後直接對定義所在的靜態類別叫用擴充方法。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ac6-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ac6-111">See also</span></span>

- [<span data-ttu-id="b1ac6-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b1ac6-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b1ac6-113">擴充方法</span><span class="sxs-lookup"><span data-stu-id="b1ac6-113">Extension Methods</span></span>](./extension-methods.md)
