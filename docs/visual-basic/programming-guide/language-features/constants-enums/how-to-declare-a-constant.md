---
title: "如何︰ 宣告常數 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.constant
dev_langs:
- VB
helpviewer_keywords:
- Integer data type, declaring constants
- Single data type, declaring constants
- Const statement [Visual Basic], declaring constants
- procedures, declaration
- data types [Visual Basic], constants
- Long data type, declaring constants
- Visual Basic code, declaring variables and constants
- Double data type, declaring constants
- Boolean data type, declaring constants
- modules, declaring constants
- Byte data type, declaring constants
- constants, declaring
- Date data type, declaring constants
- String data type, declaring constants
- declaring constants, const keyword
- Currency data type, declaring constants and variants
- module-level constants and variables
- Object data type, declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: b7fc499336c2b5db3b4d2fe9c0cd11799ea0ad77
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="cc90b-102">如何：宣告常數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc90b-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="cc90b-103">您使用`Const`陳述式來宣告常數，並將其值。</span><span class="sxs-lookup"><span data-stu-id="cc90b-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="cc90b-104">藉由宣告為常數，您可以指派有意義的名稱的值。</span><span class="sxs-lookup"><span data-stu-id="cc90b-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="cc90b-105">一旦宣告為常數，它無法修改或指派新值。</span><span class="sxs-lookup"><span data-stu-id="cc90b-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="cc90b-106">您可以宣告程序或模組、 類別或結構的宣告區段中的常數。</span><span class="sxs-lookup"><span data-stu-id="cc90b-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="cc90b-107">類別或結構層級常數`Private`根據預設，但是也可能會宣告為`Public`， `Friend`， `Protected`，或`Protected Friend`適當的層級的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="cc90b-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="cc90b-108">常數必須包含有效的符號名稱 （規則會建立變數名稱相同），以及組成的數值或字串常數和運算子 （但沒有函式呼叫） 運算式。</span><span class="sxs-lookup"><span data-stu-id="cc90b-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="cc90b-109">若要宣告常數</span><span class="sxs-lookup"><span data-stu-id="cc90b-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="cc90b-110">撰寫包含存取指定名稱的宣告`Const`關鍵字，且運算式，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="cc90b-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     <span data-ttu-id="cc90b-111">[!code-vb[VbEnumsTask #&8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc90b-111">[!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span></span>  
  
     <span data-ttu-id="cc90b-112">當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`和[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告常數，指定的資料型別 (`Boolean`， `Byte`， `Char`， `DateTime`， `Decimal`， `Double`， `Integer`， `Long`， `Short`， `Single`，或`String`)。</span><span class="sxs-lookup"><span data-stu-id="cc90b-112">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="cc90b-113">當`Option Infer`是`On`或`Option Strict`是`Off`，您可以宣告但未指定的資料類型的常數`As`子句。</span><span class="sxs-lookup"><span data-stu-id="cc90b-113">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="cc90b-114">編譯器會判斷運算式的型別常數的類型。</span><span class="sxs-lookup"><span data-stu-id="cc90b-114">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="cc90b-115">如需詳細資訊，請參閱[常數和常值的資料型別](constant-and-literal-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cc90b-115">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="cc90b-116">若要宣告具有明確陳述的資料類型的常數</span><span class="sxs-lookup"><span data-stu-id="cc90b-116">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="cc90b-117">撰寫包含宣告`As`關鍵字和明確的資料類型，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="cc90b-117">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     <span data-ttu-id="cc90b-118">[!code-vb[VbEnumsTask #&9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc90b-118">[!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span></span>  
  
     <span data-ttu-id="cc90b-119">雖然您的程式碼的可讀性宣告只有每行一個常數，您可以在同一行中，宣告多個常數。</span><span class="sxs-lookup"><span data-stu-id="cc90b-119">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="cc90b-120">如果您在同一行宣告多個常數，必須都是相同的存取層級 (`Public`， `Private`， `Friend`， `Protected`，或`Protected Friend`)。</span><span class="sxs-lookup"><span data-stu-id="cc90b-120">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="cc90b-121">若要在同一行宣告多個常數</span><span class="sxs-lookup"><span data-stu-id="cc90b-121">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="cc90b-122">分隔各個宣告使用逗號和空格，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="cc90b-122">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cc90b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc90b-123">See Also</span></span>  
 <span data-ttu-id="cc90b-124">[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cc90b-124">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="cc90b-125"> [常數和常值資料類型](constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="cc90b-125"> [Constant and Literal Data Types](constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="cc90b-126"> [常數的概觀](constants-overview.md)
 [如何︰ 宣告常數](how-to-declare-a-constant.md)
 [使用者定義常數](user-defined-constants.md)
 [常數和常值的資料型別](constant-and-literal-data-types.md)
 [如何︰ 群組關聯的常數值一起](how-to-group-related-constant-values-together.md)
 [列舉類型的概觀](enumerations-overview.md)
 [如何︰ 宣告列舉](how-to-declare-enumerations.md)
 [如何︰ 參考列舉成員](how-to-refer-to-an-enumeration-member.md)
 [列舉型別和名稱限定](enumerations-and-name-qualification.md)
 [如何︰ 逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)
 [How to︰ 判斷字串列舉值相關聯](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [何時使用列舉型別](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="cc90b-126"> [Constants Overview](constants-overview.md)
 [How to: Declare A Constant](how-to-declare-a-constant.md)
 [User-Defined Constants](user-defined-constants.md)
 [Constant and Literal Data Types](constant-and-literal-data-types.md)
 [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md)
 [Enumerations Overview](enumerations-overview.md)
 [How to: Declare Enumerations](how-to-declare-enumerations.md)
 [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md)
 [Enumerations and Name Qualification](enumerations-and-name-qualification.md)
 [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md)
 [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 <span data-ttu-id="cc90b-127">[列舉類型的概觀](enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="cc90b-127">[Enumerations Overview](enumerations-overview.md) </span></span>  
<span data-ttu-id="cc90b-128"> [常數的概觀](constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="cc90b-128"> [Constants Overview](constants-overview.md) </span></span>  
<span data-ttu-id="cc90b-129"> [如何︰ 宣告列舉類型](how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="cc90b-129"> [How to: Declare an Enumeration](how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="cc90b-130"> [列舉型別和名稱限定](enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="cc90b-130"> [Enumerations and Name Qualification](enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="cc90b-131"> [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cc90b-131"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="cc90b-132"> [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="cc90b-132"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>

