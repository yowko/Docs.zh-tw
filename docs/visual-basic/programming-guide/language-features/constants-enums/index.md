---
title: "Visual Basic 的常數和列舉類型"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants, enumerations
- naming conventions, constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ef8ade1100bb660af4d968d4b600aba41073fc2
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="49c5b-102">Visual Basic 的常數和列舉類型</span><span class="sxs-lookup"><span data-stu-id="49c5b-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="49c5b-103">常數是指使用有意義的名稱來取代維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="49c5b-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="49c5b-104">如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="49c5b-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="49c5b-105">您可以使用常數來提供有意義的名稱，而不是數字，讓程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="49c5b-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="49c5b-106">列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。</span><span class="sxs-lookup"><span data-stu-id="49c5b-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="49c5b-107">例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。</span><span class="sxs-lookup"><span data-stu-id="49c5b-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49c5b-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="49c5b-108">In This Section</span></span>  
  
|<span data-ttu-id="49c5b-109">詞彙</span><span class="sxs-lookup"><span data-stu-id="49c5b-109">Term</span></span>|<span data-ttu-id="49c5b-110">定義</span><span class="sxs-lookup"><span data-stu-id="49c5b-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="49c5b-111">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="49c5b-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="49c5b-112">本節中的主題描述常數及其用途。</span><span class="sxs-lookup"><span data-stu-id="49c5b-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="49c5b-113">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="49c5b-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="49c5b-114">本節中的主題描述列舉及其用途。</span><span class="sxs-lookup"><span data-stu-id="49c5b-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="49c5b-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="49c5b-115">Related Sections</span></span>  
  
|<span data-ttu-id="49c5b-116">詞彙</span><span class="sxs-lookup"><span data-stu-id="49c5b-116">Term</span></span>|<span data-ttu-id="49c5b-117">定義</span><span class="sxs-lookup"><span data-stu-id="49c5b-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="49c5b-118">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="49c5b-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="49c5b-119">描述 `Const` 陳述式，該陳述式可用來宣告常數。</span><span class="sxs-lookup"><span data-stu-id="49c5b-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="49c5b-120">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="49c5b-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="49c5b-121">描述 `Enum` 陳述式，該陳述式可用來建立列舉。</span><span class="sxs-lookup"><span data-stu-id="49c5b-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="49c5b-122">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="49c5b-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="49c5b-123">描述 `Option Explicit` 陳述式，該陳述式可在模組層級用來強制明確宣告該模組中的所有變數。</span><span class="sxs-lookup"><span data-stu-id="49c5b-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="49c5b-124">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="49c5b-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="49c5b-125">描述 `Option Infer` 陳述式，該陳述式可讓您在宣告變數時使用區域型別推斷。</span><span class="sxs-lookup"><span data-stu-id="49c5b-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="49c5b-126">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="49c5b-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="49c5b-127">描述 `Option Strict` 陳述式，該陳述式會將隱含資料類型轉換僅限於擴展轉換，而且不允許晚期繫結及產生`Object` 類型的隱含類型。</span><span class="sxs-lookup"><span data-stu-id="49c5b-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|

