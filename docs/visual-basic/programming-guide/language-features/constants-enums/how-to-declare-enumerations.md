---
title: 如何：宣告列舉
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 752b425ba32efe41a1ab1aa75de20039d36f5e50
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058894"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="b79fa-102">如何：宣告列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b79fa-102">How to: Declare Enumerations (Visual Basic)</span></span>

<span data-ttu-id="b79fa-103">您可以使用 `Enum` 類別或模組之宣告區段中的語句來建立列舉。</span><span class="sxs-lookup"><span data-stu-id="b79fa-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="b79fa-104">您無法在方法內宣告列舉。</span><span class="sxs-lookup"><span data-stu-id="b79fa-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="b79fa-105">若要指定適當的存取層級，請使用 `Private` 、、 `Protected` `Friend` 或 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="b79fa-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="b79fa-106">`Enum`型別具有名稱、基礎類型和一組欄位，每個都代表一個常數。</span><span class="sxs-lookup"><span data-stu-id="b79fa-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="b79fa-107">名稱必須是有效的 Visual Basic .NET 限定詞。</span><span class="sxs-lookup"><span data-stu-id="b79fa-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="b79fa-108">基礎類型必須是其中一個整數類型： `Byte` 、 `Short` `Long` 或 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="b79fa-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="b79fa-109">`Integer` 是預設值。</span><span class="sxs-lookup"><span data-stu-id="b79fa-109">`Integer` is the default.</span></span> <span data-ttu-id="b79fa-110">列舉一律為強型別，而且無法與整數類型交換。</span><span class="sxs-lookup"><span data-stu-id="b79fa-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="b79fa-111">列舉不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="b79fa-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="b79fa-112">如果列舉型別指派了浮點值，就會 `Option Strict On` 產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="b79fa-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="b79fa-113">如果 `Option Strict` 為 `Off` ，則值會自動轉換成 `Enum` 類型。</span><span class="sxs-lookup"><span data-stu-id="b79fa-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="b79fa-114">如需名稱的相關資訊，以及如何使用 `Imports` 語句來限定名稱限定性，請參閱列舉 [和名稱限定](enumerations-and-name-qualification.md)性。</span><span class="sxs-lookup"><span data-stu-id="b79fa-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="b79fa-115">宣告列舉</span><span class="sxs-lookup"><span data-stu-id="b79fa-115">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="b79fa-116">撰寫包含程式碼存取層級、 `Enum` 關鍵字和有效名稱的宣告，如下列範例所示，每個宣告都是不同的 `Enum` 。</span><span class="sxs-lookup"><span data-stu-id="b79fa-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="b79fa-117">定義列舉中的常數。</span><span class="sxs-lookup"><span data-stu-id="b79fa-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="b79fa-118">根據預設，列舉中的第一個常數會初始化為 `0` ，而且後續的常數會初始化為比上一個常數還多的值。</span><span class="sxs-lookup"><span data-stu-id="b79fa-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="b79fa-119">例如，下列列舉會包含名為的常數、以值命名的常數 `Days` `Sunday` `0` `Monday` `1` 、以的值命名的常數， `Tuesday` `2` 依此類推。</span><span class="sxs-lookup"><span data-stu-id="b79fa-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="b79fa-120">您可以使用指派語句，將值明確指派給列舉中的常數。</span><span class="sxs-lookup"><span data-stu-id="b79fa-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="b79fa-121">您可以指派包含負數的任何整數值。</span><span class="sxs-lookup"><span data-stu-id="b79fa-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="b79fa-122">例如，您可能想要值小於零的常數來表示錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="b79fa-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="b79fa-123">在下列列舉中， `Invalid` 會明確地將值指派給常數 `–1` ，並將 `Sunday` 值指派給常數 `0` 。</span><span class="sxs-lookup"><span data-stu-id="b79fa-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="b79fa-124">因為它是列舉中的第一個常數，所以 `Saturday` 也會初始化為值 `0` 。</span><span class="sxs-lookup"><span data-stu-id="b79fa-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="b79fa-125">的值 `Monday` `1` (一個以上的值 `Sunday`) ; 的值 `Tuesday` 為 `2` ，依此類推。</span><span class="sxs-lookup"><span data-stu-id="b79fa-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="b79fa-126">將列舉宣告為明確類型</span><span class="sxs-lookup"><span data-stu-id="b79fa-126">To declare an enumeration as an explicit type</span></span>  
  
- <span data-ttu-id="b79fa-127">使用子句來指定列舉的型別 `As` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b79fa-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b79fa-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b79fa-128">See also</span></span>

- [<span data-ttu-id="b79fa-129">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="b79fa-129">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="b79fa-130">如何：參考列舉類型成員</span><span class="sxs-lookup"><span data-stu-id="b79fa-130">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b79fa-131">如何：在 Visual Basic 中逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="b79fa-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="b79fa-132">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="b79fa-132">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="b79fa-133">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="b79fa-133">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="b79fa-134">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="b79fa-134">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="b79fa-135">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="b79fa-135">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="b79fa-136">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="b79fa-136">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
