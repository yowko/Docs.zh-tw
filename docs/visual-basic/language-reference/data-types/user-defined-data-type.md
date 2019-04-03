---
title: 使用者定義資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 5fe12d18c7f403c1a50ed548a260ba39e83280eb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814186"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="4d524-102">使用者定義資料類型</span><span class="sxs-lookup"><span data-stu-id="4d524-102">User-Defined Data Type</span></span>
<span data-ttu-id="4d524-103">在您定義的格式保存資料。</span><span class="sxs-lookup"><span data-stu-id="4d524-103">Holds data in a format you define.</span></span> <span data-ttu-id="4d524-104">`Structure`陳述式定義的格式。</span><span class="sxs-lookup"><span data-stu-id="4d524-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="4d524-105">舊版的 Visual Basic 支援使用者定義的型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="4d524-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="4d524-106">目前的版本會擴展 UDT*結構*。</span><span class="sxs-lookup"><span data-stu-id="4d524-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="4d524-107">結構是一或多個串連*成員*的各種資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d524-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="4d524-108">Visual Basic 會將結構視為單一單位，雖然您也可以個別地存取其成員。</span><span class="sxs-lookup"><span data-stu-id="4d524-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d524-109">備註</span><span class="sxs-lookup"><span data-stu-id="4d524-109">Remarks</span></span>  
 <span data-ttu-id="4d524-110">定義和使用結構的資料類型，當您需要將各種資料型別結合成單一單位，或沒有任何基礎資料類型提供您的需求。</span><span class="sxs-lookup"><span data-stu-id="4d524-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="4d524-111">結構的資料類型的預設值是由每個成員的預設值的組合所組成。</span><span class="sxs-lookup"><span data-stu-id="4d524-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="4d524-112">宣告格式</span><span class="sxs-lookup"><span data-stu-id="4d524-112">Declaration Format</span></span>  
 <span data-ttu-id="4d524-113">結構宣告的開頭[Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)，並結束`End Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4d524-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="4d524-114">`Structure`陳述式提供結構，這也是結構定義資料類型的識別項的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d524-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="4d524-115">其他部分的程式碼可以使用這個識別碼，來宣告變數、 參數和函式會傳回這個結構的資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="4d524-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="4d524-116">宣告之間`Structure`和`End Structure`陳述式定義的結構成員。</span><span class="sxs-lookup"><span data-stu-id="4d524-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="4d524-117">成員存取層級</span><span class="sxs-lookup"><span data-stu-id="4d524-117">Member Access Levels</span></span>  
 <span data-ttu-id="4d524-118">您必須使用每個成員的宣告[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)或陳述式，指定存取層級，例如[公用](../../../visual-basic/language-reference/modifiers/public.md)， [Friend](../../../visual-basic/language-reference/modifiers/friend.md)，或[私用](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="4d524-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="4d524-119">如果您使用`Dim`陳述式中，為公用存取層級預設值。</span><span class="sxs-lookup"><span data-stu-id="4d524-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="4d524-120">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="4d524-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="4d524-121">**記憶體耗用量。**</span><span class="sxs-lookup"><span data-stu-id="4d524-121">**Memory Consumption.**</span></span> <span data-ttu-id="4d524-122">如同所有的複合資料類型，您無法合併其成員的名義上的儲存體配置，安全地計算結構的總記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="4d524-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="4d524-123">此外，您無法安全地假設在記憶體中的儲存體的順序是您宣告的順序相同。</span><span class="sxs-lookup"><span data-stu-id="4d524-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="4d524-124">如果您需要控制結構的儲存體配置，您可以申請<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性設定為`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4d524-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="4d524-125">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="4d524-125">**Interop Considerations.**</span></span> <span data-ttu-id="4d524-126">如果您要使用的不是針對.NET Framework 撰寫的元件，例如 Automation 或 COM 物件，請記住，在其他環境中的 使用者定義型別不相容於 Visual Basic 結構類型。</span><span class="sxs-lookup"><span data-stu-id="4d524-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="4d524-127">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="4d524-127">**Widening.**</span></span> <span data-ttu-id="4d524-128">沒有自動轉換至或從任何結構的資料型別。</span><span class="sxs-lookup"><span data-stu-id="4d524-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="4d524-129">您可以定義轉換運算子，在您使用結構[Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)，而您可以宣告為每個轉換運算子`Widening`或`Narrowing`。</span><span class="sxs-lookup"><span data-stu-id="4d524-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="4d524-130">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="4d524-130">**Type Characters.**</span></span> <span data-ttu-id="4d524-131">結構的資料類型會有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="4d524-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="4d524-132">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="4d524-132">**Framework Type.**</span></span> <span data-ttu-id="4d524-133">.NET Framework 中沒有任何對應的型別。</span><span class="sxs-lookup"><span data-stu-id="4d524-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="4d524-134">所有的結構會繼承自.NET Framework 類別<xref:System.ValueType?displayProperty=nameWithType>，但沒有個別的結構會對應至<xref:System.ValueType?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4d524-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d524-135">範例</span><span class="sxs-lookup"><span data-stu-id="4d524-135">Example</span></span>  
 <span data-ttu-id="4d524-136">下列範例說明結構宣告的外框。</span><span class="sxs-lookup"><span data-stu-id="4d524-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d524-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d524-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="4d524-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="4d524-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="4d524-139">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="4d524-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="4d524-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="4d524-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="4d524-141">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="4d524-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="4d524-142">Widening</span><span class="sxs-lookup"><span data-stu-id="4d524-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="4d524-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="4d524-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="4d524-144">結構</span><span class="sxs-lookup"><span data-stu-id="4d524-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="4d524-145">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="4d524-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
