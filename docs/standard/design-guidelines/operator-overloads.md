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
ms.openlocfilehash: 893b7d1f76dfb059a0ddca77dfd8654812e9ae12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289729"
---
# <a name="operator-overloads"></a><span data-ttu-id="23c36-102">運算子多載</span><span class="sxs-lookup"><span data-stu-id="23c36-102">Operator Overloads</span></span>
<span data-ttu-id="23c36-103">運算子多載可讓架構類型看起來像是內建的語言基本專案。</span><span class="sxs-lookup"><span data-stu-id="23c36-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="23c36-104">雖然在某些情況下允許且有用，但應該謹慎使用運算子多載。</span><span class="sxs-lookup"><span data-stu-id="23c36-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="23c36-105">在許多情況下，會濫用運算子多載，例如當架構設計工具開始使用運算子進行應該是簡單方法的作業時。</span><span class="sxs-lookup"><span data-stu-id="23c36-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="23c36-106">下列指導方針可協助您決定何時及如何使用運算子多載。</span><span class="sxs-lookup"><span data-stu-id="23c36-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="23c36-107">❌請避免定義運算子多載，但不包括在應該類似基本（內建）類型的類型中。</span><span class="sxs-lookup"><span data-stu-id="23c36-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="23c36-108">✔️請考慮在型別中定義運算子多載，而該類型應該類似于基本類型。</span><span class="sxs-lookup"><span data-stu-id="23c36-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="23c36-109">例如， <xref:System.String?displayProperty=nameWithType> 已 `operator==` 定義和 `operator!=` 。</span><span class="sxs-lookup"><span data-stu-id="23c36-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="23c36-110">✔️確實在代表數位的結構中定義運算子多載（例如 <xref:System.Decimal?displayProperty=nameWithType> ）。</span><span class="sxs-lookup"><span data-stu-id="23c36-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="23c36-111">❌定義運算子多載時，不要太刻意。</span><span class="sxs-lookup"><span data-stu-id="23c36-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="23c36-112">當運算子多載立即明顯明瞭作業的結果時，它會很有用。</span><span class="sxs-lookup"><span data-stu-id="23c36-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="23c36-113">例如，能夠從另一個減去一個並取得，是合理的 <xref:System.DateTime> `DateTime` <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="23c36-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="23c36-114">不過，不適合使用邏輯 union 運算子來結合兩個資料庫查詢，或使用 shift 運算子寫入資料流程。</span><span class="sxs-lookup"><span data-stu-id="23c36-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="23c36-115">❌除非至少有一個運算元是定義多載的類型，否則請勿提供運算子多載。</span><span class="sxs-lookup"><span data-stu-id="23c36-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="23c36-116">✔️以對稱方式執行多載運算子。</span><span class="sxs-lookup"><span data-stu-id="23c36-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="23c36-117">例如，如果您多載 `operator==` ，您也應該多載 `operator!=` 。</span><span class="sxs-lookup"><span data-stu-id="23c36-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="23c36-118">同樣地，如果您多載 `operator<` ，您也應該多載 `operator>` ，依此類推。</span><span class="sxs-lookup"><span data-stu-id="23c36-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="23c36-119">✔️請考慮提供具有對應于每個多載運算子之易記名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="23c36-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="23c36-120">許多語言都不支援運算子多載。</span><span class="sxs-lookup"><span data-stu-id="23c36-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="23c36-121">基於這個理由，建議多載運算子的型別包含次要方法，並具有適當的網域特定名稱，以提供對等的功能。</span><span class="sxs-lookup"><span data-stu-id="23c36-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="23c36-122">下表包含運算子清單和對應的易記方法名稱。</span><span class="sxs-lookup"><span data-stu-id="23c36-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="23c36-123">C # 運算子符號</span><span class="sxs-lookup"><span data-stu-id="23c36-123">C# Operator Symbol</span></span>|<span data-ttu-id="23c36-124">中繼資料名稱</span><span class="sxs-lookup"><span data-stu-id="23c36-124">Metadata Name</span></span>|<span data-ttu-id="23c36-125">易記名稱</span><span class="sxs-lookup"><span data-stu-id="23c36-125">Friendly Name</span></span>|
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

### <a name="overloading-operator-"></a><span data-ttu-id="23c36-126">多載運算子 = =</span><span class="sxs-lookup"><span data-stu-id="23c36-126">Overloading Operator ==</span></span>
 <span data-ttu-id="23c36-127">多載非常 `operator ==` 複雜。</span><span class="sxs-lookup"><span data-stu-id="23c36-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="23c36-128">運算子的語義必須與數個其他成員相容，例如 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="23c36-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="23c36-129">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="23c36-129">Conversion Operators</span></span>
 <span data-ttu-id="23c36-130">轉換運算子是一元運算子，允許從某種類型轉換成另一種類型。</span><span class="sxs-lookup"><span data-stu-id="23c36-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="23c36-131">運算子必須定義為運算元或傳回類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="23c36-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="23c36-132">轉換運算子有兩種類型：隱含和明確。</span><span class="sxs-lookup"><span data-stu-id="23c36-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="23c36-133">❌如果使用者不清楚預期這類轉換，請勿提供轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="23c36-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="23c36-134">❌請勿在類型的網域外部定義轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="23c36-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="23c36-135">例如，、 <xref:System.Int32> <xref:System.Double> 和 <xref:System.Decimal> 都是數數值型別，而不是 <xref:System.DateTime> 。</span><span class="sxs-lookup"><span data-stu-id="23c36-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="23c36-136">因此，不應該有轉換運算子來將轉換成 `Double(long)` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="23c36-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="23c36-137">在這種情況下，建議使用「函式」。</span><span class="sxs-lookup"><span data-stu-id="23c36-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="23c36-138">❌如果轉換可能有損失真，請不要提供隱含轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="23c36-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="23c36-139">例如，不應該有從到的隱含轉換， `Double` `Int32` 因為的 `Double` 範圍比更寬 `Int32` 。</span><span class="sxs-lookup"><span data-stu-id="23c36-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="23c36-140">即使轉換可能有損失真，也可以提供明確轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="23c36-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="23c36-141">❌請勿從隱含轉換擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="23c36-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="23c36-142">使用者很難以瞭解發生了什麼事，因為他們可能不知道轉換正在進行中。</span><span class="sxs-lookup"><span data-stu-id="23c36-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="23c36-143"><xref:System.InvalidCastException?displayProperty=nameWithType>如果對 cast 運算子的呼叫導致損失真轉換，且運算子的合約不允許損失真轉換，✔️會擲回。</span><span class="sxs-lookup"><span data-stu-id="23c36-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="23c36-144">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="23c36-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="23c36-145">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="23c36-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="23c36-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23c36-146">See also</span></span>

- [<span data-ttu-id="23c36-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="23c36-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="23c36-148">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="23c36-148">Framework Design Guidelines</span></span>](index.md)
