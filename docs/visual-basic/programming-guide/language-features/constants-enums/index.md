---
title: 常數和列舉
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
ms.openlocfilehash: 7d15c46c0f6bb00c23dd98e464f61a5f94b0773a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414398"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="9c4ae-102">Visual Basic 的常數和列舉類型</span><span class="sxs-lookup"><span data-stu-id="9c4ae-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="9c4ae-103">常數是指使用有意義的名稱來取代維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="9c4ae-104">如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="9c4ae-105">您可以使用常數來提供有意義的名稱，而不是數字，讓程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="9c4ae-106">列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="9c4ae-107">例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c4ae-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="9c4ae-108">In This Section</span></span>  
  
|<span data-ttu-id="9c4ae-109">詞彙</span><span class="sxs-lookup"><span data-stu-id="9c4ae-109">Term</span></span>|<span data-ttu-id="9c4ae-110">定義</span><span class="sxs-lookup"><span data-stu-id="9c4ae-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="9c4ae-111">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="9c4ae-111">Constants Overview</span></span>](constants-overview.md)|<span data-ttu-id="9c4ae-112">本節中的主題描述常數及其用途。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="9c4ae-113">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="9c4ae-113">Enumerations Overview</span></span>](enumerations-overview.md)|<span data-ttu-id="9c4ae-114">本節中的主題描述列舉及其用途。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="9c4ae-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="9c4ae-115">Related Sections</span></span>  
  
|<span data-ttu-id="9c4ae-116">詞彙</span><span class="sxs-lookup"><span data-stu-id="9c4ae-116">Term</span></span>|<span data-ttu-id="9c4ae-117">定義</span><span class="sxs-lookup"><span data-stu-id="9c4ae-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="9c4ae-118">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c4ae-118">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="9c4ae-119">描述 `Const` 陳述式，該陳述式可用來宣告常數。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="9c4ae-120">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c4ae-120">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)|<span data-ttu-id="9c4ae-121">描述 `Enum` 陳述式，該陳述式可用來建立列舉。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="9c4ae-122">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c4ae-122">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="9c4ae-123">描述 `Option Explicit` 陳述式，該陳述式可在模組層級用來強制明確宣告該模組中的所有變數。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="9c4ae-124">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c4ae-124">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)|<span data-ttu-id="9c4ae-125">描述 `Option Infer` 陳述式，該陳述式可讓您在宣告變數時使用區域型別推斷。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="9c4ae-126">Long</span><span class="sxs-lookup"><span data-stu-id="9c4ae-126">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="9c4ae-127">描述 `Option Strict` 陳述式，該陳述式會將隱含資料類型轉換僅限於擴展轉換，而且不允許晚期繫結及產生`Object` 類型的隱含類型。</span><span class="sxs-lookup"><span data-stu-id="9c4ae-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
