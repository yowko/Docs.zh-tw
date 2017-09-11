---
title: "常數的概觀 (Visual Basic) |Microsoft 文件"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2df21b9e3e814c654b355472aa645481060c6f68
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="48432-102">常數的概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48432-102">Constants Overview (Visual Basic)</span></span>
<span data-ttu-id="48432-103">常數是有意義的名稱來取代數字或字串，不會變更。</span><span class="sxs-lookup"><span data-stu-id="48432-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="48432-104">常數用來儲存，正如其名，維持應用程式的執行過程中相同的值。</span><span class="sxs-lookup"><span data-stu-id="48432-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="48432-105">您可以大幅提高您的程式碼的可讀性，並使它更易於維護藉由使用常數。</span><span class="sxs-lookup"><span data-stu-id="48432-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="48432-106">在包含的值會重複出現的程式碼中使用它們，或這取決於某些很難記住或沒有明顯意義的數字。</span><span class="sxs-lookup"><span data-stu-id="48432-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="48432-107">如何建立和使用常數</span><span class="sxs-lookup"><span data-stu-id="48432-107">How to Create and Use Constants</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="48432-108">包含許多預先定義的常數，主要用於列印或顯示。</span><span class="sxs-lookup"><span data-stu-id="48432-108"> contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="48432-109">您也可以建立自己的常數與`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="48432-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="48432-110">如果`Option Strict`是`On`，您必須明確宣告常數的類型。</span><span class="sxs-lookup"><span data-stu-id="48432-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="48432-111">常數的範圍，也就是變數的可以參考它完全不需限定其名稱的所有程式碼，是變數的在相同的位置所宣告相同。</span><span class="sxs-lookup"><span data-stu-id="48432-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="48432-112">若要建立特定的程序的範圍內的常數，請在該程序宣告。</span><span class="sxs-lookup"><span data-stu-id="48432-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="48432-113">若要建立一個常數，代表可在整個應用程式，會將它宣告使用`Public`類別的宣告區段中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="48432-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48432-114">雖然常數有點類似變數，您無法修改它們，或將新值指派給它們，如同您變數。</span><span class="sxs-lookup"><span data-stu-id="48432-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="48432-115">您在程式碼中使用的常數可以定義的物件模型的控制項或元件，或它們可以是使用者定義 （也就是您自己建立）。</span><span class="sxs-lookup"><span data-stu-id="48432-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="48432-116">編譯時期和執行階段常數</span><span class="sxs-lookup"><span data-stu-id="48432-116">Compile-time and Run-time Constants</span></span>  
 <span data-ttu-id="48432-117">編譯時期常數是在編譯程式碼，而執行階段常數僅計算，在執行應用程式的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="48432-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="48432-118">編譯時期常數會每次應用程式執行時，雖然執行階段常數可能會變更每次有相同的值。</span><span class="sxs-lookup"><span data-stu-id="48432-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="48432-119">編譯時期常數是必要的例如陣列界限、 case 運算式或列舉值初始設定式。</span><span class="sxs-lookup"><span data-stu-id="48432-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48432-120">本章節內容</span><span class="sxs-lookup"><span data-stu-id="48432-120">In This Section</span></span>  
  
|<span data-ttu-id="48432-121">定義</span><span class="sxs-lookup"><span data-stu-id="48432-121">Definition</span></span>|<span data-ttu-id="48432-122">詞彙</span><span class="sxs-lookup"><span data-stu-id="48432-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="48432-123">如何：宣告常數</span><span class="sxs-lookup"><span data-stu-id="48432-123">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|<span data-ttu-id="48432-124">說明如何使用`Const`陳述式來宣告常數，並設定其值; 藉由宣告為常數，您必須指派有意義的名稱的值。</span><span class="sxs-lookup"><span data-stu-id="48432-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="48432-125">使用者定義的常數</span><span class="sxs-lookup"><span data-stu-id="48432-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|<span data-ttu-id="48432-126">描述如何建立您自己的常數，包括設定範圍的詳細資訊，以及如何避免循環參考。</span><span class="sxs-lookup"><span data-stu-id="48432-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="48432-127">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="48432-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|<span data-ttu-id="48432-128">如何提供有關[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器初始化常數時`Option Explicit`已關閉。</span><span class="sxs-lookup"><span data-stu-id="48432-128">Provides information on how the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="48432-129">如何：將關聯的常數值群組在一起</span><span class="sxs-lookup"><span data-stu-id="48432-129">How to: Group Related Constant Values Together</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|<span data-ttu-id="48432-130">示範如何以群組相關的常數值。</span><span class="sxs-lookup"><span data-stu-id="48432-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="48432-131">參考資料</span><span class="sxs-lookup"><span data-stu-id="48432-131">Reference</span></span>  
  
|<span data-ttu-id="48432-132">定義</span><span class="sxs-lookup"><span data-stu-id="48432-132">Definition</span></span>|<span data-ttu-id="48432-133">詞彙</span><span class="sxs-lookup"><span data-stu-id="48432-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="48432-134">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="48432-134">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|<span data-ttu-id="48432-135">列出預先定義的常數[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="48432-135">Lists the constants predefined by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>|  
|[<span data-ttu-id="48432-136">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="48432-136">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="48432-137">描述`Const`陳述式和它的用法。</span><span class="sxs-lookup"><span data-stu-id="48432-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="48432-138">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="48432-138">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="48432-139">描述`Option Strict`陳述式和它的用法。</span><span class="sxs-lookup"><span data-stu-id="48432-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48432-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48432-140">See Also</span></span>  
 <span data-ttu-id="48432-141">[列舉類型的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="48432-141">[Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="48432-142"> [如何︰ 在 Visual Basic 中的將陣列變數初始化](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span><span class="sxs-lookup"><span data-stu-id="48432-142"> [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span></span>
