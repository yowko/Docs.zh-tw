---
title: 作法：明確實作介面成員 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5ef8b42fe5ca07548d52b88720ea4845d2408bb1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589202"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="dbfc6-102">作法：明確實作介面成員 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="dbfc6-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="dbfc6-103">這個範例會宣告[介面](../../language-reference/keywords/interface.md) (`IDimensions`) 和類別 (`Box`)，它會明確實作介面成員 `getLength` 和 `getWidth`。</span><span class="sxs-lookup"><span data-stu-id="dbfc6-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="dbfc6-104">成員是透過介面執行個體 `dimensions` 存取。</span><span class="sxs-lookup"><span data-stu-id="dbfc6-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbfc6-105">範例</span><span class="sxs-lookup"><span data-stu-id="dbfc6-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="dbfc6-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="dbfc6-106">Robust Programming</span></span>  
  
- <span data-ttu-id="dbfc6-107">請注意，在 `Main` 方法中，下列各行因為會產生編譯錯誤所以都已註解。</span><span class="sxs-lookup"><span data-stu-id="dbfc6-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="dbfc6-108">從[類別](../../language-reference/keywords/class.md)執行個體無法存取已明確實作的介面成員：</span><span class="sxs-lookup"><span data-stu-id="dbfc6-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="dbfc6-109">另請注意，在 `Main` 方法中，下列幾行會成功列印方塊大小，因為正從介面的執行個體呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="dbfc6-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="dbfc6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbfc6-110">See also</span></span>

- [<span data-ttu-id="dbfc6-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dbfc6-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dbfc6-112">類別和結構</span><span class="sxs-lookup"><span data-stu-id="dbfc6-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="dbfc6-113">介面</span><span class="sxs-lookup"><span data-stu-id="dbfc6-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="dbfc6-114">如何：明確實作兩個介面的成員</span><span class="sxs-lookup"><span data-stu-id="dbfc6-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
