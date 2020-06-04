---
title: 使用者定義資料類型
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
ms.openlocfilehash: fbd9536a54d7fb471d6cb2e130b14a84e40a4940
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415488"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="0e1be-102">使用者定義資料類型</span><span class="sxs-lookup"><span data-stu-id="0e1be-102">User-Defined Data Type</span></span>

<span data-ttu-id="0e1be-103">以您定義的格式來保存資料。</span><span class="sxs-lookup"><span data-stu-id="0e1be-103">Holds data in a format you define.</span></span> <span data-ttu-id="0e1be-104">`Structure`語句會定義格式。</span><span class="sxs-lookup"><span data-stu-id="0e1be-104">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="0e1be-105">舊版的 Visual Basic 支援使用者定義型別（UDT）。</span><span class="sxs-lookup"><span data-stu-id="0e1be-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="0e1be-106">目前的版本會將 UDT 擴充至*結構*。</span><span class="sxs-lookup"><span data-stu-id="0e1be-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="0e1be-107">結構是一或多個不同資料類型*成員*的串連。</span><span class="sxs-lookup"><span data-stu-id="0e1be-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="0e1be-108">Visual Basic 會將結構視為單一單位，不過您也可以個別存取其成員。</span><span class="sxs-lookup"><span data-stu-id="0e1be-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e1be-109">備註</span><span class="sxs-lookup"><span data-stu-id="0e1be-109">Remarks</span></span>

<span data-ttu-id="0e1be-110">當您需要將各種資料類型結合成單一單位，或沒有任何基本資料類型滿足您的需求時，請定義和使用結構資料類型。</span><span class="sxs-lookup"><span data-stu-id="0e1be-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="0e1be-111">結構資料類型的預設值是由其每個成員的預設值組合所組成。</span><span class="sxs-lookup"><span data-stu-id="0e1be-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="0e1be-112">宣告格式</span><span class="sxs-lookup"><span data-stu-id="0e1be-112">Declaration Format</span></span>

<span data-ttu-id="0e1be-113">結構宣告會以[結構語句](../statements/structure-statement.md)開頭，並以語句結尾 `End Structure` 。</span><span class="sxs-lookup"><span data-stu-id="0e1be-113">A structure declaration starts with the [Structure Statement](../statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="0e1be-114">`Structure`語句會提供結構的名稱，這也是結構所定義之資料類型的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0e1be-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="0e1be-115">程式碼的其他部分可以使用此識別碼來宣告變數、參數和函式傳回值，使其成為此結構的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0e1be-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="0e1be-116">和語句之間的宣告會 `Structure` `End Structure` 定義結構的成員。</span><span class="sxs-lookup"><span data-stu-id="0e1be-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="0e1be-117">成員存取層級</span><span class="sxs-lookup"><span data-stu-id="0e1be-117">Member Access Levels</span></span>

<span data-ttu-id="0e1be-118">您必須使用[Dim 語句](../statements/dim-statement.md)或指定存取層級的語句（例如[Public](../modifiers/public.md)、 [Friend](../modifiers/friend.md)或[Private](../modifiers/private.md)）來宣告每個成員。</span><span class="sxs-lookup"><span data-stu-id="0e1be-118">You must declare every member using a [Dim Statement](../statements/dim-statement.md) or a statement that specifies access level, such as [Public](../modifiers/public.md), [Friend](../modifiers/friend.md), or [Private](../modifiers/private.md).</span></span> <span data-ttu-id="0e1be-119">如果您使用 `Dim` 語句，存取層級預設為 [公用]。</span><span class="sxs-lookup"><span data-stu-id="0e1be-119">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="0e1be-120">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="0e1be-120">Programming Tips</span></span>

- <span data-ttu-id="0e1be-121">**記憶體耗用量。**</span><span class="sxs-lookup"><span data-stu-id="0e1be-121">**Memory Consumption.**</span></span> <span data-ttu-id="0e1be-122">如同所有複合資料型別，您無法安全地計算結構的總記憶體耗用量，方法是將其成員的名義儲存體配置相加。</span><span class="sxs-lookup"><span data-stu-id="0e1be-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="0e1be-123">此外，您無法安全地假設記憶體中的儲存順序與您的宣告順序相同。</span><span class="sxs-lookup"><span data-stu-id="0e1be-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="0e1be-124">如果您需要控制結構的儲存配置，您可以將 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性套用至 `Structure` 語句。</span><span class="sxs-lookup"><span data-stu-id="0e1be-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="0e1be-125">**Interop 考量：**</span><span class="sxs-lookup"><span data-stu-id="0e1be-125">**Interop Considerations.**</span></span> <span data-ttu-id="0e1be-126">如果您要使用的元件不是針對 .NET Framework 所撰寫（例如 Automation 或 COM 物件），請記住，其他環境中的使用者定義類型與 Visual Basic 結構類型不相容。</span><span class="sxs-lookup"><span data-stu-id="0e1be-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="0e1be-127">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="0e1be-127">**Widening.**</span></span> <span data-ttu-id="0e1be-128">沒有任何結構資料類型的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="0e1be-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="0e1be-129">您可以使用[運算子語句](../statements/operator-statement.md)定義結構上的轉換運算子，也可以將每個轉換運算子宣告為 `Widening` 或 `Narrowing` 。</span><span class="sxs-lookup"><span data-stu-id="0e1be-129">You can define conversion operators on your structure using the [Operator Statement](../statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="0e1be-130">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="0e1be-130">**Type Characters.**</span></span> <span data-ttu-id="0e1be-131">結構資料類型沒有常數值型別字元或識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="0e1be-131">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="0e1be-132">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="0e1be-132">**Framework Type.**</span></span> <span data-ttu-id="0e1be-133">.NET Framework 中沒有對應的類型。</span><span class="sxs-lookup"><span data-stu-id="0e1be-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="0e1be-134">所有結構都會繼承自 .NET Framework 類別 <xref:System.ValueType?displayProperty=nameWithType> ，但不會對應到任何個別結構 <xref:System.ValueType?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0e1be-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="0e1be-135">範例</span><span class="sxs-lookup"><span data-stu-id="0e1be-135">Example</span></span>

<span data-ttu-id="0e1be-136">下列範例顯示結構宣告的外框。</span><span class="sxs-lookup"><span data-stu-id="0e1be-136">The following paradigm shows the outline of the declaration of a structure.</span></span>

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="0e1be-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e1be-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="0e1be-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="0e1be-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="0e1be-139">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="0e1be-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="0e1be-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="0e1be-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="0e1be-141">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="0e1be-141">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="0e1be-142">Widening</span><span class="sxs-lookup"><span data-stu-id="0e1be-142">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="0e1be-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="0e1be-143">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="0e1be-144">結構</span><span class="sxs-lookup"><span data-stu-id="0e1be-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0e1be-145">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="0e1be-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
