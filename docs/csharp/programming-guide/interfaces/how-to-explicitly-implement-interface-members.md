---
title: 如何明確執行介面成員-程式C#設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 4efc325b3587ee790cce739727506a28c3a1f524
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635401"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="2a2b1-102">如何明確執行介面成員（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="2a2b1-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="2a2b1-103">這個範例會宣告[介面](../../language-reference/keywords/interface.md) (`IDimensions`) 和類別 (`Box`)，它會明確實作介面成員 `getLength` 和 `getWidth`。</span><span class="sxs-lookup"><span data-stu-id="2a2b1-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="2a2b1-104">成員是透過介面執行個體 `dimensions` 存取。</span><span class="sxs-lookup"><span data-stu-id="2a2b1-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a2b1-105">範例</span><span class="sxs-lookup"><span data-stu-id="2a2b1-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2a2b1-106">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="2a2b1-106">Robust Programming</span></span>  
  
- <span data-ttu-id="2a2b1-107">請注意，在 `Main` 方法中，下列各行因為會產生編譯錯誤所以都已註解。</span><span class="sxs-lookup"><span data-stu-id="2a2b1-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="2a2b1-108">從[類別](../../language-reference/keywords/class.md)執行個體無法存取已明確實作的介面成員：</span><span class="sxs-lookup"><span data-stu-id="2a2b1-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="2a2b1-109">另請注意，在 `Main` 方法中，下列幾行會成功列印方塊大小，因為正從介面的執行個體呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="2a2b1-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="2a2b1-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a2b1-110">See also</span></span>

- [<span data-ttu-id="2a2b1-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2a2b1-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2a2b1-112">類別和結構</span><span class="sxs-lookup"><span data-stu-id="2a2b1-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="2a2b1-113">介面</span><span class="sxs-lookup"><span data-stu-id="2a2b1-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="2a2b1-114">如何明確地執行兩個介面的成員</span><span class="sxs-lookup"><span data-stu-id="2a2b1-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
