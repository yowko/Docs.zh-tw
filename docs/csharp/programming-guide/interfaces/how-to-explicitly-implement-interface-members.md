---
title: 如何：明確實作介面成員 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5f7ae6bae46cdf6596b206abbdeeb94b5c21a13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332182"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="29b4e-102">如何：明確實作介面成員 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="29b4e-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="29b4e-103">這個範例會宣告[介面](../../../csharp/language-reference/keywords/interface.md) (`IDimensions`) 和類別 (`Box`)，它會明確實作介面成員 `getLength` 和 `getWidth`。</span><span class="sxs-lookup"><span data-stu-id="29b4e-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="29b4e-104">成員是透過介面執行個體 `dimensions` 存取。</span><span class="sxs-lookup"><span data-stu-id="29b4e-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29b4e-105">範例</span><span class="sxs-lookup"><span data-stu-id="29b4e-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="29b4e-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="29b4e-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="29b4e-107">請注意，在 `Main` 方法中，下列各行因為會產生編譯錯誤所以都已註解。</span><span class="sxs-lookup"><span data-stu-id="29b4e-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="29b4e-108">從[類別](../../../csharp/language-reference/keywords/class.md)執行個體無法存取已明確實作的介面成員：</span><span class="sxs-lookup"><span data-stu-id="29b4e-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="29b4e-109">另請注意，在 `Main` 方法中，下列幾行會成功列印方塊大小，因為正從介面的執行個體呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="29b4e-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="29b4e-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="29b4e-110">See Also</span></span>  
 [<span data-ttu-id="29b4e-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="29b4e-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="29b4e-112">類別和結構</span><span class="sxs-lookup"><span data-stu-id="29b4e-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="29b4e-113">介面</span><span class="sxs-lookup"><span data-stu-id="29b4e-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="29b4e-114">如何：明確實作兩個介面的成員</span><span class="sxs-lookup"><span data-stu-id="29b4e-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
