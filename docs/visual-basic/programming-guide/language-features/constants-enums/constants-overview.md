---
title: 常數概觀
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 7f2a2dc140352588246d80a7feb46ce1f609b358
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086279"
---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="d9991-102">常數的概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9991-102">Constants Overview (Visual Basic)</span></span>

<span data-ttu-id="d9991-103">常數是有意義的名稱，用來取代未變更的數位或字串。</span><span class="sxs-lookup"><span data-stu-id="d9991-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="d9991-104">常數儲存的值（如名稱所示）在應用程式的整個執行過程中都保持不變。</span><span class="sxs-lookup"><span data-stu-id="d9991-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="d9991-105">您可以大幅提升程式碼的可讀性，並讓您更輕鬆地使用常數進行維護。</span><span class="sxs-lookup"><span data-stu-id="d9991-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="d9991-106">在程式碼中使用它們，這些值會重新出現或取決於難以記住或沒有明顯意義的特定數位。</span><span class="sxs-lookup"><span data-stu-id="d9991-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="d9991-107">如何建立和使用常數</span><span class="sxs-lookup"><span data-stu-id="d9991-107">How to Create and Use Constants</span></span>  

 <span data-ttu-id="d9991-108">Visual Basic 包含許多預先定義的常數，主要是用來列印和顯示。</span><span class="sxs-lookup"><span data-stu-id="d9991-108">Visual Basic contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="d9991-109">您也可以使用語句來建立自己的常數 `Const` ，並使用您用來建立變數名稱的相同指導方針。</span><span class="sxs-lookup"><span data-stu-id="d9991-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="d9991-110">如果 `Option Strict` 為 `On` ，則您必須明確宣告常數型別。</span><span class="sxs-lookup"><span data-stu-id="d9991-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="d9991-111">常數的範圍，也就是一組可以參考它而不限定其名稱的程式碼，與在相同位置中宣告的變數相同。</span><span class="sxs-lookup"><span data-stu-id="d9991-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="d9991-112">若要建立存在於特定程式範圍內的常數，請在該程式內宣告它。</span><span class="sxs-lookup"><span data-stu-id="d9991-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="d9991-113">若要建立可在整個應用程式中使用的常數，請 `Public` 在類別的宣告區段中使用關鍵字來宣告。</span><span class="sxs-lookup"><span data-stu-id="d9991-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9991-114">雖然常數有點類似變數，但您無法修改它們或指派新值給它們，就像您可以變數一樣。</span><span class="sxs-lookup"><span data-stu-id="d9991-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="d9991-115">您在程式碼中使用的常數可以由您使用之控制項或元件的物件模型定義，也可以是使用者定義的 (也就是您自行建立的) 。</span><span class="sxs-lookup"><span data-stu-id="d9991-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="d9991-116">編譯時期和執行時間常數</span><span class="sxs-lookup"><span data-stu-id="d9991-116">Compile-time and Run-time Constants</span></span>  

 <span data-ttu-id="d9991-117">編譯時期常數是在編譯器代碼時計算，而執行時間常數則只能在應用程式執行時進行計算。</span><span class="sxs-lookup"><span data-stu-id="d9991-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="d9991-118">在每次執行應用程式時，編譯時期常數都有相同的值，而執行時間常數可能會每次變更。</span><span class="sxs-lookup"><span data-stu-id="d9991-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="d9991-119">針對陣列界限、case 運算式或枚舉器初始化運算式等案例，需要編譯時間常數。</span><span class="sxs-lookup"><span data-stu-id="d9991-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9991-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="d9991-120">In This Section</span></span>  
  
|<span data-ttu-id="d9991-121">定義</span><span class="sxs-lookup"><span data-stu-id="d9991-121">Definition</span></span>|<span data-ttu-id="d9991-122">詞彙</span><span class="sxs-lookup"><span data-stu-id="d9991-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="d9991-123">如何：宣告常數</span><span class="sxs-lookup"><span data-stu-id="d9991-123">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)|<span data-ttu-id="d9991-124">說明如何使用 `Const` 語句來宣告常數並設定其值; 您可以藉由宣告常數，將有意義的名稱指派給值。</span><span class="sxs-lookup"><span data-stu-id="d9991-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="d9991-125">使用者定義的常數</span><span class="sxs-lookup"><span data-stu-id="d9991-125">User-Defined Constants</span></span>](user-defined-constants.md)|<span data-ttu-id="d9991-126">描述如何建立您自己的常數，包括範圍的資訊，以及如何避免迴圈參考。</span><span class="sxs-lookup"><span data-stu-id="d9991-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="d9991-127">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="d9991-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)|<span data-ttu-id="d9991-128">提供當關閉時，Visual Basic 編譯器如何初始化常數的相關資訊 `Option Explicit` 。</span><span class="sxs-lookup"><span data-stu-id="d9991-128">Provides information on how the Visual Basic compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="d9991-129">如何：將關聯的常數值群組在一起</span><span class="sxs-lookup"><span data-stu-id="d9991-129">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)|<span data-ttu-id="d9991-130">示範如何將相關的常數值分組。</span><span class="sxs-lookup"><span data-stu-id="d9991-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="d9991-131">參考</span><span class="sxs-lookup"><span data-stu-id="d9991-131">Reference</span></span>  
  
|<span data-ttu-id="d9991-132">定義</span><span class="sxs-lookup"><span data-stu-id="d9991-132">Definition</span></span>|<span data-ttu-id="d9991-133">詞彙</span><span class="sxs-lookup"><span data-stu-id="d9991-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="d9991-134">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="d9991-134">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)|<span data-ttu-id="d9991-135">列出 Visual Basic 預先定義的常數。</span><span class="sxs-lookup"><span data-stu-id="d9991-135">Lists the constants predefined by Visual Basic.</span></span>|  
|[<span data-ttu-id="d9991-136">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="d9991-136">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="d9991-137">描述 `Const` 語句及其用法。</span><span class="sxs-lookup"><span data-stu-id="d9991-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="d9991-138">Long</span><span class="sxs-lookup"><span data-stu-id="d9991-138">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="d9991-139">描述 `Option Strict` 語句及其用法。</span><span class="sxs-lookup"><span data-stu-id="d9991-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9991-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9991-140">See also</span></span>

- [<span data-ttu-id="d9991-141">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="d9991-141">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="d9991-142">如何：在 Visual Basic 中初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="d9991-142">How to: Initialize an Array Variable in Visual Basic</span></span>](../arrays/how-to-initialize-an-array-variable.md)
