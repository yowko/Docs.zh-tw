---
title: 作法：建立列舉類型的新方法 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 99a2005e1a64fa214776145a903341fb162f0633
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597053"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="a91a2-102">作法：建立列舉類型的新方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a91a2-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="a91a2-103">您可以使用擴充方法來新增專屬於特定列舉類型的功能。</span><span class="sxs-lookup"><span data-stu-id="a91a2-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a91a2-104">範例</span><span class="sxs-lookup"><span data-stu-id="a91a2-104">Example</span></span>  
 <span data-ttu-id="a91a2-105">在下例中，`Grades` 列舉代表班上學生可能得到的字母分級成績。</span><span class="sxs-lookup"><span data-stu-id="a91a2-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="a91a2-106">已將名為 `Passing` 的擴充方法新增至 `Grades` 類型，以便該類型的每個執行個體現在都「知道」它是否代表傳遞等級。</span><span class="sxs-lookup"><span data-stu-id="a91a2-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="a91a2-107">請注意，`Extensions` 類別也包含動態更新的靜態變數，以及反映該變數目前值的擴充方法傳回值。</span><span class="sxs-lookup"><span data-stu-id="a91a2-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="a91a2-108">本例示範，在幕後直接對定義所在的靜態類別叫用擴充方法。</span><span class="sxs-lookup"><span data-stu-id="a91a2-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91a2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a91a2-109">See also</span></span>

- [<span data-ttu-id="a91a2-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a91a2-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a91a2-111">擴充方法</span><span class="sxs-lookup"><span data-stu-id="a91a2-111">Extension Methods</span></span>](./extension-methods.md)
