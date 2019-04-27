---
title: 常數的概觀 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2939110de77718baf32e2a0d8f1aa52dba997cf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907084"
---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="72b90-102">常數的概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b90-102">Constants Overview (Visual Basic)</span></span>
<span data-ttu-id="72b90-103">常數是有意義的名稱來取代數字或字串，不會變更。</span><span class="sxs-lookup"><span data-stu-id="72b90-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="72b90-104">常數用來儲存值，如同名稱所暗示，維持不變執行作業的應用程式。</span><span class="sxs-lookup"><span data-stu-id="72b90-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="72b90-105">您可以大幅改善您的程式碼的可讀性，並輕鬆地維護藉由使用常數。</span><span class="sxs-lookup"><span data-stu-id="72b90-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="72b90-106">在包含的值會重複出現的程式碼中使用它們，或相依於某些很難記住，或沒有任何明顯的意義的數字。</span><span class="sxs-lookup"><span data-stu-id="72b90-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="72b90-107">如何建立和使用常數</span><span class="sxs-lookup"><span data-stu-id="72b90-107">How to Create and Use Constants</span></span>  
 <span data-ttu-id="72b90-108">Visual Basic 會包含許多預先定義的常數，主要用於列印與顯示。</span><span class="sxs-lookup"><span data-stu-id="72b90-108">Visual Basic contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="72b90-109">您也可以建立自己的常數，與`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="72b90-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="72b90-110">如果`Option Strict`是`On`，您必須明確宣告常數的類型。</span><span class="sxs-lookup"><span data-stu-id="72b90-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="72b90-111">常數的範圍內，也就是變數的可以參考未限定其名稱的所有程式碼的集合，是變數的在相同的位置所宣告相同。</span><span class="sxs-lookup"><span data-stu-id="72b90-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="72b90-112">若要建立特定的程序的範圍內存在的常數，請在該程序內宣告。</span><span class="sxs-lookup"><span data-stu-id="72b90-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="72b90-113">若要建立一個常數，代表可在整個應用程式，將它使用宣告`Public`類別的 「 宣告 」 區段中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="72b90-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72b90-114">雖然常數有點類似於變數，您無法修改它們，或將新的值指派給它們，如同您變數。</span><span class="sxs-lookup"><span data-stu-id="72b90-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="72b90-115">您在您的程式碼中使用的常數可以定義控制項或元件使用的物件模型，或它們可以是使用者定義 （也就是您建立您自己）。</span><span class="sxs-lookup"><span data-stu-id="72b90-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="72b90-116">編譯時期和執行階段常數</span><span class="sxs-lookup"><span data-stu-id="72b90-116">Compile-time and Run-time Constants</span></span>  
 <span data-ttu-id="72b90-117">編譯時期常數是在程式碼會編譯，而應用程式執行時，您可以只將計算的執行階段常數時間來計算。</span><span class="sxs-lookup"><span data-stu-id="72b90-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="72b90-118">每次應用程式執行時，雖然執行階段常數可能會在每次變更時，編譯時間常數會有相同的值。</span><span class="sxs-lookup"><span data-stu-id="72b90-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="72b90-119">編譯時期常數不需要在陣列界限，case 運算式或列舉值的初始設定式的情況。</span><span class="sxs-lookup"><span data-stu-id="72b90-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72b90-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="72b90-120">In This Section</span></span>  
  
|<span data-ttu-id="72b90-121">定義</span><span class="sxs-lookup"><span data-stu-id="72b90-121">Definition</span></span>|<span data-ttu-id="72b90-122">詞彙</span><span class="sxs-lookup"><span data-stu-id="72b90-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="72b90-123">如何：宣告常數</span><span class="sxs-lookup"><span data-stu-id="72b90-123">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|<span data-ttu-id="72b90-124">說明如何使用`Const`陳述式來宣告常數，並將它的值; 藉由宣告為常數，您必須指派有意義的名稱的值。</span><span class="sxs-lookup"><span data-stu-id="72b90-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="72b90-125">使用者定義的常數</span><span class="sxs-lookup"><span data-stu-id="72b90-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|<span data-ttu-id="72b90-126">描述如何建立您自己的常數，包括設定範圍的詳細資訊，以及如何避免循環參考。</span><span class="sxs-lookup"><span data-stu-id="72b90-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="72b90-127">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="72b90-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|<span data-ttu-id="72b90-128">提供有關 Visual Basic 編譯器如何初始化常數時`Option Explicit`已關閉。</span><span class="sxs-lookup"><span data-stu-id="72b90-128">Provides information on how the Visual Basic compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="72b90-129">如何：群組關聯的常數值在一起</span><span class="sxs-lookup"><span data-stu-id="72b90-129">How to: Group Related Constant Values Together</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|<span data-ttu-id="72b90-130">示範如何將群組相關的常數值。</span><span class="sxs-lookup"><span data-stu-id="72b90-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="72b90-131">參考資料</span><span class="sxs-lookup"><span data-stu-id="72b90-131">Reference</span></span>  
  
|<span data-ttu-id="72b90-132">定義</span><span class="sxs-lookup"><span data-stu-id="72b90-132">Definition</span></span>|<span data-ttu-id="72b90-133">詞彙</span><span class="sxs-lookup"><span data-stu-id="72b90-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="72b90-134">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="72b90-134">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|<span data-ttu-id="72b90-135">列出預先定義的 Visual basic 的常數。</span><span class="sxs-lookup"><span data-stu-id="72b90-135">Lists the constants predefined by Visual Basic.</span></span>|  
|[<span data-ttu-id="72b90-136">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="72b90-136">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="72b90-137">描述`Const`陳述式和它的用法。</span><span class="sxs-lookup"><span data-stu-id="72b90-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="72b90-138">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="72b90-138">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="72b90-139">描述`Option Strict`陳述式和它的用法。</span><span class="sxs-lookup"><span data-stu-id="72b90-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72b90-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72b90-140">See also</span></span>

- [<span data-ttu-id="72b90-141">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="72b90-141">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="72b90-142">如何：初始化陣列變數在 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72b90-142">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
