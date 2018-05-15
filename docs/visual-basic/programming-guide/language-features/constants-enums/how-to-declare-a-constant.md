---
title: 如何：宣告常數 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: ce45e4df7f74cd68bde0fb2adba10197a11edb1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="09793-102">如何：宣告常數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09793-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="09793-103">您使用`Const`陳述式來宣告常數，並將其值設定。</span><span class="sxs-lookup"><span data-stu-id="09793-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="09793-104">藉由宣告為常數，您可以指派有意義的名稱的值。</span><span class="sxs-lookup"><span data-stu-id="09793-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="09793-105">一旦已宣告為常數，它不能修改或指派新值。</span><span class="sxs-lookup"><span data-stu-id="09793-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="09793-106">您宣告常數程序內或在模組、 類別或結構的宣告區段中。</span><span class="sxs-lookup"><span data-stu-id="09793-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="09793-107">類別或結構層級常數`Private`根據預設，但也可能會宣告為`Public`， `Friend`， `Protected`，或`Protected Friend`適當層級的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="09793-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="09793-108">常數必須包含有效的符號名稱 （規則會建立變數名稱相同），以及組成的數值或字串常數和運算子 （但沒有函式呼叫） 運算式。</span><span class="sxs-lookup"><span data-stu-id="09793-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="09793-109">若要宣告常數</span><span class="sxs-lookup"><span data-stu-id="09793-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="09793-110">寫入包含存取指定名稱的宣告`Const`關鍵字和運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="09793-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     <span data-ttu-id="09793-111">當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`和[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告為常數，藉由指定的資料類型 (`Boolean`， `Byte`， `Char`， `DateTime`， `Decimal`， `Double`， `Integer`， `Long`， `Short`， `Single`，或`String`)。</span><span class="sxs-lookup"><span data-stu-id="09793-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="09793-112">當`Option Infer`是`On`或`Option Strict`是`Off`，您可以宣告常數但未指定的資料型別`As`子句。</span><span class="sxs-lookup"><span data-stu-id="09793-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="09793-113">編譯器會判斷運算式的型別常數的類型。</span><span class="sxs-lookup"><span data-stu-id="09793-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="09793-114">如需詳細資訊，請參閱[常數和常值的資料型別](constant-and-literal-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="09793-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="09793-115">若要宣告常數有明確陳述的資料類型</span><span class="sxs-lookup"><span data-stu-id="09793-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="09793-116">撰寫包含宣告`As`關鍵字和明確的資料類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="09793-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     <span data-ttu-id="09793-117">雖然您的程式碼更容易閱讀如果您宣告僅每行一個常數，您可以在單一行中，宣告多個常數。</span><span class="sxs-lookup"><span data-stu-id="09793-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="09793-118">如果您宣告多個常數在單一行，則必須有相同的存取層級 (`Public`， `Private`， `Friend`， `Protected`，或`Protected Friend`)。</span><span class="sxs-lookup"><span data-stu-id="09793-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="09793-119">若要在單行中宣告多個常數</span><span class="sxs-lookup"><span data-stu-id="09793-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="09793-120">分隔宣告使用逗號和空格，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="09793-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="09793-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09793-121">See Also</span></span>  
 [<span data-ttu-id="09793-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="09793-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="09793-123">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="09793-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)  
 <span data-ttu-id="09793-124">[常數的概觀](constants-overview.md)[如何： 宣告常數](how-to-declare-a-constant.md)[使用者定義常數](user-defined-constants.md)[常數和常值的資料型別](constant-and-literal-data-types.md) [How to： 群組相互關聯的常數值](how-to-group-related-constant-values-together.md)[列舉類型的概觀](enumerations-overview.md)[如何： 宣告列舉](how-to-declare-enumerations.md)[如何： 參考列舉成員](how-to-refer-to-an-enumeration-member.md)[列舉型別和名稱限定](enumerations-and-name-qualification.md)[如何： 逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)[如何： 決定與列舉值關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)[何時使用列舉](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="09793-124">[Constants Overview](constants-overview.md) [How to: Declare A Constant](how-to-declare-a-constant.md) [User-Defined Constants](user-defined-constants.md) [Constant and Literal Data Types](constant-and-literal-data-types.md) [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md) [Enumerations Overview](enumerations-overview.md) [How to: Declare Enumerations](how-to-declare-enumerations.md) [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md) [Enumerations and Name Qualification](enumerations-and-name-qualification.md) [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md) [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md) [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 [<span data-ttu-id="09793-125">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="09793-125">Enumerations Overview</span></span>](enumerations-overview.md)  
 [<span data-ttu-id="09793-126">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="09793-126">Constants Overview</span></span>](constants-overview.md)  
 [<span data-ttu-id="09793-127">如何： 宣告列舉</span><span class="sxs-lookup"><span data-stu-id="09793-127">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)  
 [<span data-ttu-id="09793-128">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="09793-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)  
 [<span data-ttu-id="09793-129">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="09793-129">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="09793-130">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="09793-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
