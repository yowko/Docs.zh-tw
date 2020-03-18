---
title: 運算子多載
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400565"
---
# <a name="operator-overloads"></a><span data-ttu-id="57e81-102">運算子多載</span><span class="sxs-lookup"><span data-stu-id="57e81-102">Operator Overloads</span></span>
<span data-ttu-id="57e81-103">運算子多載允許框架類型顯示為內置語言基元。</span><span class="sxs-lookup"><span data-stu-id="57e81-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="57e81-104">儘管在某些情況下允許並且很有用，但應謹慎使用操作員超載。</span><span class="sxs-lookup"><span data-stu-id="57e81-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="57e81-105">在許多情況下，運算子超載被濫用，例如框架設計器開始使用運算子執行應該簡單的操作。</span><span class="sxs-lookup"><span data-stu-id="57e81-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="57e81-106">以下指南將説明您決定何時以及如何使用運算子多載。</span><span class="sxs-lookup"><span data-stu-id="57e81-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="57e81-107">❌AVOID 定義運算子多載，但應感覺像基元（內置）類型的類型除外。</span><span class="sxs-lookup"><span data-stu-id="57e81-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="57e81-108">✔️考慮在應感覺像基元類型的類型中定義運算子多載。</span><span class="sxs-lookup"><span data-stu-id="57e81-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="57e81-109">例如，<xref:System.String?displayProperty=nameWithType>已`operator==`和`operator!=`已定義。</span><span class="sxs-lookup"><span data-stu-id="57e81-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="57e81-110">✔️DO在表示數位（如<xref:System.Decimal?displayProperty=nameWithType>）的結構中定義運算子多載。</span><span class="sxs-lookup"><span data-stu-id="57e81-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="57e81-111">❌定義運算子超載時不要可愛。</span><span class="sxs-lookup"><span data-stu-id="57e81-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="57e81-112">在操作結果立即明顯的情況下，操作員重載非常有用。</span><span class="sxs-lookup"><span data-stu-id="57e81-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="57e81-113">例如，能夠從另<xref:System.DateTime>`DateTime`一個中減去一個並獲取 一個<xref:System.TimeSpan>是有意義的。</span><span class="sxs-lookup"><span data-stu-id="57e81-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="57e81-114">但是，使用邏輯聯合運算子聯合兩個資料庫查詢或使用移位運算子寫入流是不適當的。</span><span class="sxs-lookup"><span data-stu-id="57e81-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="57e81-115">❌除非至少有一個運算元是定義重載的類型，否則不要提供運算子多載。</span><span class="sxs-lookup"><span data-stu-id="57e81-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="57e81-116">✔️以對稱方式執行重載運算子。</span><span class="sxs-lookup"><span data-stu-id="57e81-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="57e81-117">例如，如果重載`operator==`， 還應重載 。 `operator!=`</span><span class="sxs-lookup"><span data-stu-id="57e81-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="57e81-118">同樣，如果重載`operator<`，也應重載`operator>`等。</span><span class="sxs-lookup"><span data-stu-id="57e81-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="57e81-119">✔️考慮提供與每個重載運算子對應的易記名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="57e81-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="57e81-120">許多語言不支援運算子多載。</span><span class="sxs-lookup"><span data-stu-id="57e81-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="57e81-121">因此，建議重載運算子的類型包括具有提供等效功能的適當特定于域的名稱的輔助方法。</span><span class="sxs-lookup"><span data-stu-id="57e81-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="57e81-122">下表包含運算子清單和相應的友好方法名稱。</span><span class="sxs-lookup"><span data-stu-id="57e81-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="57e81-123">C# 運算子符號</span><span class="sxs-lookup"><span data-stu-id="57e81-123">C# Operator Symbol</span></span>|<span data-ttu-id="57e81-124">中繼資料名稱</span><span class="sxs-lookup"><span data-stu-id="57e81-124">Metadata Name</span></span>|<span data-ttu-id="57e81-125">易記名稱</span><span class="sxs-lookup"><span data-stu-id="57e81-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="57e81-126">重載運算子 |</span><span class="sxs-lookup"><span data-stu-id="57e81-126">Overloading Operator ==</span></span>
 <span data-ttu-id="57e81-127">超載`operator ==`相當複雜。</span><span class="sxs-lookup"><span data-stu-id="57e81-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="57e81-128">運算子的語義需要與其他幾個成員（如<xref:System.Object.Equals%2A?displayProperty=nameWithType>） 相容。</span><span class="sxs-lookup"><span data-stu-id="57e81-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="57e81-129">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="57e81-129">Conversion Operators</span></span>
 <span data-ttu-id="57e81-130">轉換運算子是允許從一種類型轉換為另一種類型的單位運算子。</span><span class="sxs-lookup"><span data-stu-id="57e81-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="57e81-131">運算子必須定義為運算元或返回類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="57e81-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="57e81-132">轉換運算子有兩種類型：隱式運算子和顯式運算子。</span><span class="sxs-lookup"><span data-stu-id="57e81-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="57e81-133">❌如果最終使用者沒有明確預期此類轉換，則不要提供轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="57e81-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="57e81-134">❌不要在類型域之外定義轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="57e81-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="57e81-135"><xref:System.Int32>例如，<xref:System.Double>和<xref:System.Decimal>都是數位類型， 而不是。 <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="57e81-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="57e81-136">因此，不應有轉換運算子將`Double(long)`轉換為 。 `DateTime`</span><span class="sxs-lookup"><span data-stu-id="57e81-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="57e81-137">在這種情況下，建構函式是首選。</span><span class="sxs-lookup"><span data-stu-id="57e81-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="57e81-138">❌如果轉換可能丟失，請不要提供隱式轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="57e81-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="57e81-139">例如，`Double`不應有從 到`Int32`的隱式轉換，`Double`因為 範圍比`Int32`寬。</span><span class="sxs-lookup"><span data-stu-id="57e81-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="57e81-140">即使轉換可能丟失，也可以提供顯式轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="57e81-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="57e81-141">❌不要從隱式強制轉換中引發異常。</span><span class="sxs-lookup"><span data-stu-id="57e81-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="57e81-142">最終使用者很難理解發生了什麼，因為他們可能不知道正在進行轉換。</span><span class="sxs-lookup"><span data-stu-id="57e81-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="57e81-143">如果調用強制<xref:System.InvalidCastException?displayProperty=nameWithType>轉換運算子導致虧損轉換，並且操作員的合同不允許虧損轉換，則✔️強制進行丟棄。</span><span class="sxs-lookup"><span data-stu-id="57e81-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="57e81-144">*部分© 2005， 2009 微軟公司.保留擁有權利。*</span><span class="sxs-lookup"><span data-stu-id="57e81-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="57e81-145">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="57e81-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="57e81-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57e81-146">See also</span></span>

- [<span data-ttu-id="57e81-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="57e81-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="57e81-148">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="57e81-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
