---
title: '如何明確執行介面成員-c # 程式設計手冊'
description: '瞭解如何在此 c # 範例中明確地執行介面成員。 成員是透過介面實例來存取。'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 35b512ff6cbee1dd942f5b3476db660481808297
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303071"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="1238f-104">如何明確執行介面成員（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="1238f-104">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="1238f-105">這個範例會宣告[介面](../../language-reference/keywords/interface.md) `IDimensions` 和類別， `Box` 其會明確地執行介面成員 `GetLength` 和 `GetWidth` 。</span><span class="sxs-lookup"><span data-stu-id="1238f-105">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="1238f-106">成員是透過介面執行個體 `dimensions` 存取。</span><span class="sxs-lookup"><span data-stu-id="1238f-106">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1238f-107">範例</span><span class="sxs-lookup"><span data-stu-id="1238f-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1238f-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1238f-108">Robust Programming</span></span>  
  
- <span data-ttu-id="1238f-109">請注意，在 `Main` 方法中，下列各行因為會產生編譯錯誤所以都已註解。</span><span class="sxs-lookup"><span data-stu-id="1238f-109">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="1238f-110">從[類別](../../language-reference/keywords/class.md)執行個體無法存取已明確實作的介面成員：</span><span class="sxs-lookup"><span data-stu-id="1238f-110">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="1238f-111">另請注意，在 `Main` 方法中，下列幾行會成功列印方塊大小，因為正從介面的執行個體呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="1238f-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="1238f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1238f-112">See also</span></span>

- [<span data-ttu-id="1238f-113">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1238f-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1238f-114">類別和結構</span><span class="sxs-lookup"><span data-stu-id="1238f-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1238f-115">介面</span><span class="sxs-lookup"><span data-stu-id="1238f-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1238f-116">如何明確實作兩個介面的成員</span><span class="sxs-lookup"><span data-stu-id="1238f-116">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
