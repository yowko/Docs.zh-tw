---
title: Visual Basic 的常數和列舉類型
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: dfd9330210dd748d739cd8da2985795099beacd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646379"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="6b6f1-102">Visual Basic 的常數和列舉類型</span><span class="sxs-lookup"><span data-stu-id="6b6f1-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="6b6f1-103">常數是指使用有意義的名稱來取代維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="6b6f1-104">如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="6b6f1-105">您可以使用常數來提供有意義的名稱，而不是數字，讓程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="6b6f1-106">列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="6b6f1-107">例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b6f1-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="6b6f1-108">In This Section</span></span>  
  
|<span data-ttu-id="6b6f1-109">詞彙</span><span class="sxs-lookup"><span data-stu-id="6b6f1-109">Term</span></span>|<span data-ttu-id="6b6f1-110">定義</span><span class="sxs-lookup"><span data-stu-id="6b6f1-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="6b6f1-111">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="6b6f1-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="6b6f1-112">本節中的主題描述常數及其用途。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="6b6f1-113">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="6b6f1-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="6b6f1-114">本節中的主題描述列舉及其用途。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="6b6f1-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="6b6f1-115">Related Sections</span></span>  
  
|<span data-ttu-id="6b6f1-116">詞彙</span><span class="sxs-lookup"><span data-stu-id="6b6f1-116">Term</span></span>|<span data-ttu-id="6b6f1-117">定義</span><span class="sxs-lookup"><span data-stu-id="6b6f1-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="6b6f1-118">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b6f1-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="6b6f1-119">描述 `Const` 陳述式，該陳述式可用來宣告常數。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="6b6f1-120">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b6f1-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="6b6f1-121">描述 `Enum` 陳述式，該陳述式可用來建立列舉。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="6b6f1-122">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b6f1-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="6b6f1-123">描述 `Option Explicit` 陳述式，該陳述式可在模組層級用來強制明確宣告該模組中的所有變數。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="6b6f1-124">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b6f1-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="6b6f1-125">描述 `Option Infer` 陳述式，該陳述式可讓您在宣告變數時使用區域型別推斷。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="6b6f1-126">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b6f1-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="6b6f1-127">描述 `Option Strict` 陳述式，該陳述式會將隱含資料類型轉換僅限於擴展轉換，而且不允許晚期繫結及產生`Object` 類型的隱含類型。</span><span class="sxs-lookup"><span data-stu-id="6b6f1-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
