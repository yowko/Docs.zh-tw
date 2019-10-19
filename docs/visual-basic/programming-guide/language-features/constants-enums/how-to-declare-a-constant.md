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
ms.openlocfilehash: 8b84ab5e8edebba3048c5cddf723198cf3f28858
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579917"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="c3522-102">如何：宣告常數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3522-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="c3522-103">您可以使用 `Const` 語句來宣告常數並設定其值。</span><span class="sxs-lookup"><span data-stu-id="c3522-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="c3522-104">藉由宣告常數，您可以將有意義的名稱指派給值。</span><span class="sxs-lookup"><span data-stu-id="c3522-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="c3522-105">一旦宣告了常數，就無法修改或指派新的值。</span><span class="sxs-lookup"><span data-stu-id="c3522-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="c3522-106">您在程式內或在模組、類別或結構的宣告區段中宣告常數。</span><span class="sxs-lookup"><span data-stu-id="c3522-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="c3522-107">類別或結構層級常數預設為 `Private`，但也可以宣告為適當的程式碼存取層級 `Public`、`Friend`、`Protected` 或 `Protected Friend`。</span><span class="sxs-lookup"><span data-stu-id="c3522-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="c3522-108">常數必須具有有效的符號名稱（規則與建立變數名稱的規則相同），以及由數值或字串常數和運算子（但不含函式呼叫）組成的運算式。</span><span class="sxs-lookup"><span data-stu-id="c3522-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="c3522-109">若要宣告常數</span><span class="sxs-lookup"><span data-stu-id="c3522-109">To declare a constant</span></span>  
  
- <span data-ttu-id="c3522-110">撰寫包含存取規範、`Const` 關鍵字和運算式的宣告，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c3522-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="c3522-111">當[Option 推斷](../../../../visual-basic/language-reference/statements/option-infer-statement.md)為 `Off`，且[option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)為 `On` 時，您必須指定資料類型（`Boolean`、`Byte`、`Char`、`DateTime`、`Decimal`、`Double`、0，明確地宣告常數。、1、2、3 或 4）。</span><span class="sxs-lookup"><span data-stu-id="c3522-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="c3522-112">當 `Option Infer` `On` 或 `Option Strict` `Off` 時，您可以宣告常數，而不需使用 `As` 子句來指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="c3522-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="c3522-113">編譯器會從運算式的類型判斷常數的類型。</span><span class="sxs-lookup"><span data-stu-id="c3522-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="c3522-114">如需詳細資訊，請參閱[常數和常值資料類型](constant-and-literal-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c3522-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="c3522-115">若要宣告具有明確陳述之資料類型的常數</span><span class="sxs-lookup"><span data-stu-id="c3522-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="c3522-116">撰寫包含 `As` 關鍵字和明確資料類型的宣告，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c3522-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="c3522-117">您可以在同一行宣告多個常數，不過，如果您的程式碼在每行只宣告一個常數，則會更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="c3522-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="c3522-118">如果您在單一行上宣告多個常數，它們都必須具有相同的存取層級（`Public`、`Private`、`Friend`、`Protected` 或 `Protected Friend`）。</span><span class="sxs-lookup"><span data-stu-id="c3522-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="c3522-119">若要在同一行宣告多個常數</span><span class="sxs-lookup"><span data-stu-id="c3522-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="c3522-120">以逗號和空格分隔宣告，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c3522-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c3522-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3522-121">See also</span></span>

- [<span data-ttu-id="c3522-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="c3522-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="c3522-123">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="c3522-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="c3522-124">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="c3522-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="c3522-125">如何：宣告常數</span><span class="sxs-lookup"><span data-stu-id="c3522-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="c3522-126">使用者定義的常數</span><span class="sxs-lookup"><span data-stu-id="c3522-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="c3522-127">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="c3522-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="c3522-128">如何：將關聯的常數值群組在一起</span><span class="sxs-lookup"><span data-stu-id="c3522-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="c3522-129">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="c3522-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="c3522-130">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="c3522-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="c3522-131">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="c3522-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="c3522-132">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="c3522-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="c3522-133">如何：逐一查看列舉</span><span class="sxs-lookup"><span data-stu-id="c3522-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="c3522-134">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="c3522-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="c3522-135">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="c3522-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="c3522-136">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="c3522-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="c3522-137">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="c3522-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="c3522-138">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="c3522-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="c3522-139">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="c3522-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="c3522-140">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="c3522-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c3522-141">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="c3522-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
