---
title: 如何：宣告列舉
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 042aea045313bcaf3832274acf1000f87a084b72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354050"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="8be88-102">如何：宣告列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8be88-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="8be88-103">您可以使用類別或模組之宣告區段中的 `Enum` 語句來建立列舉。</span><span class="sxs-lookup"><span data-stu-id="8be88-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="8be88-104">您無法在方法中宣告列舉。</span><span class="sxs-lookup"><span data-stu-id="8be88-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="8be88-105">若要指定適當的存取層級，請使用 `Private`、`Protected`、`Friend`或 `Public`。</span><span class="sxs-lookup"><span data-stu-id="8be88-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="8be88-106">`Enum` 型別具有名稱、基礎型別，以及一組欄位，每個都代表一個常數。</span><span class="sxs-lookup"><span data-stu-id="8be88-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="8be88-107">此名稱必須是有效的 Visual Basic .NET 辨識符號。</span><span class="sxs-lookup"><span data-stu-id="8be88-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="8be88-108">基礎類型必須是其中一個整數類型，`Byte`、`Short`、`Long` 或 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="8be88-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="8be88-109">預設值為 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="8be88-109">`Integer` is the default.</span></span> <span data-ttu-id="8be88-110">列舉一律是強型別，而且無法與整數數位類型互換。</span><span class="sxs-lookup"><span data-stu-id="8be88-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="8be88-111">列舉不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="8be88-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="8be88-112">如果列舉已指派具有 `Option Strict On`的浮點值，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="8be88-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="8be88-113">如果 `Off``Option Strict`，此值會自動轉換成 `Enum` 類型。</span><span class="sxs-lookup"><span data-stu-id="8be88-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="8be88-114">如需名稱的相關資訊，以及如何使用 `Imports` 語句來進行不必要的名稱限定，請參閱列舉[和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)性。</span><span class="sxs-lookup"><span data-stu-id="8be88-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="8be88-115">若要宣告列舉</span><span class="sxs-lookup"><span data-stu-id="8be88-115">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="8be88-116">撰寫包含程式碼存取層級、`Enum` 關鍵字和有效名稱的宣告，如下列範例所示，每個都宣告不同的 `Enum`。</span><span class="sxs-lookup"><span data-stu-id="8be88-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="8be88-117">定義列舉中的常數。</span><span class="sxs-lookup"><span data-stu-id="8be88-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="8be88-118">根據預設，列舉中的第一個常數會初始化為 `0`，而後續的常數會初始化為比上一個常數更多的值。</span><span class="sxs-lookup"><span data-stu-id="8be88-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="8be88-119">例如，下列列舉 `Days`包含名為 `Sunday` 的常數，其值為 `0`、名為 `Monday` 且值為 `1`的常數、名為 `Tuesday` 的常數，其值為 `2`等等。</span><span class="sxs-lookup"><span data-stu-id="8be88-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="8be88-120">您可以使用指派語句，明確地將值指派給列舉中的常數。</span><span class="sxs-lookup"><span data-stu-id="8be88-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="8be88-121">您可以指派任何整數值，包括負數。</span><span class="sxs-lookup"><span data-stu-id="8be88-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="8be88-122">例如，您可能想要值小於零的常數來表示錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="8be88-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="8be88-123">在下列列舉中，會明確地將值指派給常數 `Invalid` `–1`，並將值指派給常數 `Sunday` `0`。</span><span class="sxs-lookup"><span data-stu-id="8be88-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="8be88-124">因為它是列舉中的第一個常數，所以 `Saturday` 也會初始化為 `0`的值。</span><span class="sxs-lookup"><span data-stu-id="8be88-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="8be88-125">`Monday` 的值 `1` （一個大於 `Sunday`的值）;`Tuesday` 的值為 `2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="8be88-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="8be88-126">將列舉宣告為明確類型</span><span class="sxs-lookup"><span data-stu-id="8be88-126">To declare an enumeration as an explicit type</span></span>  
  
- <span data-ttu-id="8be88-127">使用 `As` 子句來指定列舉的類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8be88-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="8be88-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="8be88-128">See also</span></span>

- [<span data-ttu-id="8be88-129">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="8be88-129">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="8be88-130">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="8be88-130">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="8be88-131">如何：在 Visual Basic 中逐一查看列舉</span><span class="sxs-lookup"><span data-stu-id="8be88-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="8be88-132">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="8be88-132">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="8be88-133">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="8be88-133">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="8be88-134">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="8be88-134">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="8be88-135">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="8be88-135">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="8be88-136">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="8be88-136">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
