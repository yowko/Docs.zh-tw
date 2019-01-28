---
title: 純函數式轉換簡介 (C#)
ms.date: 07/20/2015
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
ms.openlocfilehash: 63b7a69baeb42c82fb1c94d08cee17519330025c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501800"
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="92e9b-102">純函數式轉換簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="92e9b-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="92e9b-103">本節說明功能性轉換，包括基礎的概念與支援的語言建構。</span><span class="sxs-lookup"><span data-stu-id="92e9b-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="92e9b-104">其中包含程式設計的物件導向與功能性轉換方法，包括如何轉換到後者的建議。</span><span class="sxs-lookup"><span data-stu-id="92e9b-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="92e9b-105">雖然在許多程式設計案例中都可以使用功能性轉換，但是此處使用 XML 轉換做為具體範例。</span><span class="sxs-lookup"><span data-stu-id="92e9b-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92e9b-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="92e9b-106">In This Section</span></span>  
  
|<span data-ttu-id="92e9b-107">主題</span><span class="sxs-lookup"><span data-stu-id="92e9b-107">Topic</span></span>|<span data-ttu-id="92e9b-108">說明</span><span class="sxs-lookup"><span data-stu-id="92e9b-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="92e9b-109">概念和術語 (函數式轉換) (C#)</span><span class="sxs-lookup"><span data-stu-id="92e9b-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="92e9b-110">說明純功能性轉換的概念與術語。</span><span class="sxs-lookup"><span data-stu-id="92e9b-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="92e9b-111">函數式程式設計與命令式程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="92e9b-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="92e9b-112">比較與對照功能性程式設計與更傳統的命令性 (程序性) 程式設計。</span><span class="sxs-lookup"><span data-stu-id="92e9b-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="92e9b-113">重構為純虛擬函式 (C#)</span><span class="sxs-lookup"><span data-stu-id="92e9b-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="92e9b-114">說明純虛擬函式，並顯示純虛擬函式與非純虛擬函式的範例。</span><span class="sxs-lookup"><span data-stu-id="92e9b-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="92e9b-115">函數式轉換的適用性 (C#)</span><span class="sxs-lookup"><span data-stu-id="92e9b-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="92e9b-116">描述功能性轉換的典型案例。</span><span class="sxs-lookup"><span data-stu-id="92e9b-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="92e9b-117">XML 函數式轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92e9b-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="92e9b-118">描述轉換 XML 樹狀內容中的功能性轉換。</span><span class="sxs-lookup"><span data-stu-id="92e9b-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92e9b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92e9b-119">See also</span></span>

- [<span data-ttu-id="92e9b-120">XML 純功能性轉換 (C#)</span><span class="sxs-lookup"><span data-stu-id="92e9b-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
