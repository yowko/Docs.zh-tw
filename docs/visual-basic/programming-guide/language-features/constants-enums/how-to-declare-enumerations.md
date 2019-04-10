---
title: HOW TO：宣告列舉 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: f168d6d9cd6970353e75fa35a7e52cc7156fda72
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343333"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="b1cdf-102">HOW TO：宣告列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1cdf-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="b1cdf-103">您建立的列舉`Enum`「 宣告 」 區段中的類別或模組的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="b1cdf-104">您無法宣告列舉型別方法內。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="b1cdf-105">若要指定適當的存取等級，請使用`Private`， `Protected`， `Friend`，或`Public`。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="b1cdf-106">`Enum`型別具有名稱、 基礎類型和一組欄位，每個均代表一個常數。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="b1cdf-107">名稱必須是有效的 Visual Basic.NET 限定詞。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="b1cdf-108">基礎類型必須是整數型別 —`Byte`， `Short`，`Long`或`Integer`。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> `Integer` <span data-ttu-id="b1cdf-109">預設值。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-109">is the default.</span></span> <span data-ttu-id="b1cdf-110">列舉型別一律強型別，並不能互換使用整數數字類型。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="b1cdf-111">列舉型別不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="b1cdf-112">如果列舉型別指派的浮點值`Option Strict On`，造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="b1cdf-113">如果`Option Strict`已`Off`，值會自動轉換為`Enum`型別。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="b1cdf-114">如需名稱資訊，以及如何使用`Imports`陳述式，使名稱限定性條件不必要的請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="b1cdf-115">來宣告列舉</span><span class="sxs-lookup"><span data-stu-id="b1cdf-115">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="b1cdf-116">撰寫包含程式碼存取層級中，宣告`Enum`關鍵字，且有效的名稱，如下列範例中，其中每個宣告不同`Enum`。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="b1cdf-117">列舉中定義的常數。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="b1cdf-118">根據預設，第一個常數，列舉型別會初始化為`0`，且後續的常數會初始化為值大於先前的常數。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="b1cdf-119">比方說，下列的列舉， `Days`，包含名為的常數`Sunday`具有值`0`，名為常數`Monday`值`1`，名為常數`Tuesday`值`2`等等。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="b1cdf-120">您可以使用指派陳述式明確地指派常數列舉中的值。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="b1cdf-121">您可以指派任何整數值，包括負數的數字。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="b1cdf-122">比方說，您可以使用值小於零，表示錯誤狀況的常數。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="b1cdf-123">在下列的列舉常數`Invalid`被明確指派的值`–1`，和常數`Sunday`的值會指派給`0`。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="b1cdf-124">因為它是在列舉中，第一個常數`Saturday`也會初始化為值`0`。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="b1cdf-125">值`Monday`是`1`(其中的值超過`Sunday`); 的值`Tuesday`是`2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="b1cdf-126">若要宣告明確的型別為列舉型別</span><span class="sxs-lookup"><span data-stu-id="b1cdf-126">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="b1cdf-127">使用指定的列舉型別`As`子句，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b1cdf-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b1cdf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1cdf-128">See also</span></span>

- [<span data-ttu-id="b1cdf-129">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="b1cdf-129">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="b1cdf-130">HOW TO：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="b1cdf-130">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b1cdf-131">HOW TO：逐一查看 Visual Basic 中列舉</span><span class="sxs-lookup"><span data-stu-id="b1cdf-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="b1cdf-132">HOW TO：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="b1cdf-132">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="b1cdf-133">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="b1cdf-133">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="b1cdf-134">常數概觀</span><span class="sxs-lookup"><span data-stu-id="b1cdf-134">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="b1cdf-135">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="b1cdf-135">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="b1cdf-136">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="b1cdf-136">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
