---
title: '如何明確執行兩個介面的成員-c # 程式設計手冊'
description: '瞭解如何明確執行兩個具有相同成員名稱的介面，並在此 c # 範例中為每個介面成員提供個別的執行方式。'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: d60ec43f734d5e8bfa7f467874440bd3514877fe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303058"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="852a0-103">如何明確執行兩個介面的成員（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="852a0-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="852a0-104">明確的[介面](../../language-reference/keywords/interface.md)實作也可讓程式設計人員實作具有相同成員名稱的兩個介面，並提供每個介面成員不同的實作。</span><span class="sxs-lookup"><span data-stu-id="852a0-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="852a0-105">此範例會顯示方塊尺寸的計量和英制單位。</span><span class="sxs-lookup"><span data-stu-id="852a0-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="852a0-106">Box [類別](../../language-reference/keywords/class.md)實作 IEnglishDimensions 和 IMetricDimensions 兩個介面，代表不同的量值系統。</span><span class="sxs-lookup"><span data-stu-id="852a0-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="852a0-107">這兩個介面具有相同的成員名稱，Length 和 Width。</span><span class="sxs-lookup"><span data-stu-id="852a0-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="852a0-108">範例</span><span class="sxs-lookup"><span data-stu-id="852a0-108">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="852a0-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="852a0-109">Robust Programming</span></span>  
 <span data-ttu-id="852a0-110">如果您想要以英制單位建立預設的量值單位，請按一般方式實作 Length 和 Width 方法，並從 IMetricDimensions 介面明確實作 Length 和 Width 方法：</span><span class="sxs-lookup"><span data-stu-id="852a0-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="852a0-111">在本例中，您可以從類別執行個體存取英制單位，從介面執行個體存取計量單位：</span><span class="sxs-lookup"><span data-stu-id="852a0-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="852a0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="852a0-112">See also</span></span>

- [<span data-ttu-id="852a0-113">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="852a0-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="852a0-114">類別和結構</span><span class="sxs-lookup"><span data-stu-id="852a0-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="852a0-115">介面</span><span class="sxs-lookup"><span data-stu-id="852a0-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="852a0-116">如何明確實作介面成員</span><span class="sxs-lookup"><span data-stu-id="852a0-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
