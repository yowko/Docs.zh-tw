---
title: "如何︰ 宣告列舉 (Visual Basic) |Microsoft 文件"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
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
ms.openlocfilehash: 7adaca7e7252ce7165a5fd27b5bc9c049388206c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="1539d-102">如何：宣告列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1539d-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="1539d-103">建立列舉型別與`Enum`類別或模組的陳述式的宣告區段中。</span><span class="sxs-lookup"><span data-stu-id="1539d-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="1539d-104">您無法宣告列舉型別方法內。</span><span class="sxs-lookup"><span data-stu-id="1539d-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="1539d-105">若要指定適當的存取層級，請使用`Private`， `Protected`， `Friend`，或`Public`。</span><span class="sxs-lookup"><span data-stu-id="1539d-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="1539d-106">`Enum`型別具有名稱、 基礎型別，以及一組欄位，各代表一個常數。</span><span class="sxs-lookup"><span data-stu-id="1539d-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="1539d-107">名稱必須是有效[!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]限定詞。</span><span class="sxs-lookup"><span data-stu-id="1539d-107">The name must be a valid [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualifier.</span></span> <span data-ttu-id="1539d-108">基礎型別必須是整數類型的其中一個 —`Byte`， `Short`，`Long`或`Integer`。</span><span class="sxs-lookup"><span data-stu-id="1539d-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="1539d-109">`Integer` 是預設值。</span><span class="sxs-lookup"><span data-stu-id="1539d-109">`Integer` is the default.</span></span> <span data-ttu-id="1539d-110">列舉型別一律強型別，並不能互換使用整數的數字類型。</span><span class="sxs-lookup"><span data-stu-id="1539d-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="1539d-111">列舉型別不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="1539d-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="1539d-112">如果列舉型別指派的浮點值`Option Strict On`，造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="1539d-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="1539d-113">如果`Option Strict`是`Off`，值會自動轉換為`Enum`型別。</span><span class="sxs-lookup"><span data-stu-id="1539d-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="1539d-114">如需名稱及如何使用`Imports`陳述式，讓名稱限定不必要的請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="1539d-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="1539d-115">若要宣告列舉類型</span><span class="sxs-lookup"><span data-stu-id="1539d-115">To declare an enumeration</span></span>  
  
1.  <span data-ttu-id="1539d-116">撰寫包含程式碼存取層級宣告`Enum`關鍵字，且有效的名稱，如下列範例中，其中每個宣告不同`Enum`。</span><span class="sxs-lookup"><span data-stu-id="1539d-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     <span data-ttu-id="1539d-117">[!code-vb[VbEnumsTask #&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1539d-117">[!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span></span>  
  
2.  <span data-ttu-id="1539d-118">列舉中定義常數。</span><span class="sxs-lookup"><span data-stu-id="1539d-118">Define the constants in the enumeration.</span></span> <span data-ttu-id="1539d-119">根據預設，列舉型別的第一個常數會初始化為`0`，而之後的常數會初始化為值&1; 的上一個常數。</span><span class="sxs-lookup"><span data-stu-id="1539d-119">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="1539d-120">例如，以下列舉`Days`，包含名為常數`Sunday`值`0`，名為常數`Monday`值`1`，名為常數`Tuesday`值是`2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="1539d-120">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     <span data-ttu-id="1539d-121">[!code-vb[VbEnumsTask #&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1539d-121">[!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span></span>  
  
3.  <span data-ttu-id="1539d-122">您可以使用在指派陳述式明確地指派列舉型別常數的值。</span><span class="sxs-lookup"><span data-stu-id="1539d-122">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="1539d-123">您可以指派任何整數值，包括負數。</span><span class="sxs-lookup"><span data-stu-id="1539d-123">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="1539d-124">例如，您可以常數的值小於零來表示錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="1539d-124">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="1539d-125">在下列的列舉常數`Invalid`已明確指派值`–1`，和常數`Sunday`會指派值`0`。</span><span class="sxs-lookup"><span data-stu-id="1539d-125">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="1539d-126">因為它是列舉型別，第一個常數`Saturday`也會初始化為值`0`。</span><span class="sxs-lookup"><span data-stu-id="1539d-126">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="1539d-127">值`Monday`是`1`(的值大於`Sunday`); 的值`Tuesday`是`2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="1539d-127">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     <span data-ttu-id="1539d-128">[!code-vb[VbEnumsTask #&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1539d-128">[!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span></span>  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="1539d-129">若要宣告明確的型別為列舉型別</span><span class="sxs-lookup"><span data-stu-id="1539d-129">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="1539d-130">使用指定的列舉類型`As`子句，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1539d-130">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     <span data-ttu-id="1539d-131">[!code-vb[VbEnumsTask #&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1539d-131">[!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1539d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1539d-132">See Also</span></span>  
 <span data-ttu-id="1539d-133">[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="1539d-133">[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="1539d-134"> [如何︰ 參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="1539d-134"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="1539d-135"> [如何︰ 逐一查看在 Visual Basic 中列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="1539d-135"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="1539d-136"> [如何︰ 決定與列舉值關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="1539d-136"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="1539d-137"> [何時使用列舉型別](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="1539d-137"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="1539d-138"> [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="1539d-138"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="1539d-139"> [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1539d-139"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="1539d-140"> [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="1539d-140"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
