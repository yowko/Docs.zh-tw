---
title: 運算子多載
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 40e1c6a4a65bfc20c94223e4012e34928b25a2ab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830034"
---
# <a name="operator-overloads"></a><span data-ttu-id="45d82-102">運算子多載</span><span class="sxs-lookup"><span data-stu-id="45d82-102">Operator Overloads</span></span>
<span data-ttu-id="45d82-103">運算子多載可讓架構類型顯示為內建的語言基本類型。</span><span class="sxs-lookup"><span data-stu-id="45d82-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="45d82-104">雖然在某些情況下允許且很有用，但應該謹慎使用運算子多載。</span><span class="sxs-lookup"><span data-stu-id="45d82-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="45d82-105">在許多情況下，運算子多載已被濫用，例如，當架構設計工具開始使用運算子進行應該是簡單方法的作業時。</span><span class="sxs-lookup"><span data-stu-id="45d82-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="45d82-106">下列指導方針可協助您決定何時及如何使用運算子多載。</span><span class="sxs-lookup"><span data-stu-id="45d82-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="45d82-107">❌ 請避免定義運算子多載，但應該類似基本 (內建) 類型的類型除外。</span><span class="sxs-lookup"><span data-stu-id="45d82-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="45d82-108">✔️考慮定義型別中的運算子多載，而該型別應該會像基本型別一樣。</span><span class="sxs-lookup"><span data-stu-id="45d82-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="45d82-109">例如， <xref:System.String?displayProperty=nameWithType> 具有 `operator==` 和已 `operator!=` 定義。</span><span class="sxs-lookup"><span data-stu-id="45d82-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="45d82-110">✔️在代表數位 (的結構中定義運算子多載，例如 <xref:System.Decimal?displayProperty=nameWithType>) 。</span><span class="sxs-lookup"><span data-stu-id="45d82-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="45d82-111">❌ 在定義運算子多載時，請勿刻意進行。</span><span class="sxs-lookup"><span data-stu-id="45d82-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="45d82-112">運算子多載很有用，因為在這種情況下，作業的結果將會立即被察覺。</span><span class="sxs-lookup"><span data-stu-id="45d82-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="45d82-113">例如，您可以從另一個減去另一個， <xref:System.DateTime> `DateTime` 然後取得 <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="45d82-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="45d82-114">但是，不適合使用邏輯 union 運算子來 union 兩個資料庫查詢，或使用 shift 運算子來寫入資料流程。</span><span class="sxs-lookup"><span data-stu-id="45d82-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="45d82-115">❌ 除非至少有一個運算元的類型是定義多載，否則請勿提供運算子多載。</span><span class="sxs-lookup"><span data-stu-id="45d82-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="45d82-116">✔️以對稱方式進行多載運算子。</span><span class="sxs-lookup"><span data-stu-id="45d82-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="45d82-117">例如，如果您多載 `operator==` ，您也應該多載 `operator!=` 。</span><span class="sxs-lookup"><span data-stu-id="45d82-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="45d82-118">同樣地，如果您多載 `operator<` ，您也應該多載 `operator>` ，依此類推。</span><span class="sxs-lookup"><span data-stu-id="45d82-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="45d82-119">✔️考慮提供具有易記名稱的方法，這些方法會對應至每個多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="45d82-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="45d82-120">許多語言不支援運算子多載。</span><span class="sxs-lookup"><span data-stu-id="45d82-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="45d82-121">基於這個理由，建議多載運算子的型別包含具有適當特定網功能變數名稱稱的次要方法，以提供對等的功能。</span><span class="sxs-lookup"><span data-stu-id="45d82-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="45d82-122">下表包含運算子清單和對應的易記方法名稱。</span><span class="sxs-lookup"><span data-stu-id="45d82-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="45d82-123">C # 運算子符號</span><span class="sxs-lookup"><span data-stu-id="45d82-123">C# Operator Symbol</span></span>|<span data-ttu-id="45d82-124">中繼資料名稱</span><span class="sxs-lookup"><span data-stu-id="45d82-124">Metadata Name</span></span>|<span data-ttu-id="45d82-125">易記名稱</span><span class="sxs-lookup"><span data-stu-id="45d82-125">Friendly Name</span></span>|
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

### <a name="overloading-operator-"></a><span data-ttu-id="45d82-126">多載運算子 = =</span><span class="sxs-lookup"><span data-stu-id="45d82-126">Overloading Operator ==</span></span>
 <span data-ttu-id="45d82-127">多載 `operator ==` 相當複雜。</span><span class="sxs-lookup"><span data-stu-id="45d82-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="45d82-128">運算子的語法必須與其他數個成員相容，例如 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="45d82-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="45d82-129">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="45d82-129">Conversion Operators</span></span>
 <span data-ttu-id="45d82-130">轉換運算子是一元運算子，可允許從某個類型轉換成另一個類型。</span><span class="sxs-lookup"><span data-stu-id="45d82-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="45d82-131">運算子必須定義為運算元或傳回型別上的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="45d82-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="45d82-132">轉換運算子有兩種類型：隱含和明確。</span><span class="sxs-lookup"><span data-stu-id="45d82-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="45d82-133">❌ 如果終端使用者無法明確地預期這類轉換，請不要提供轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="45d82-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="45d82-134">❌ 請勿定義型別網域以外的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="45d82-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="45d82-135">例如，、 <xref:System.Int32> <xref:System.Double> 和 <xref:System.Decimal> 都是數數值型別，而 <xref:System.DateTime> 不是。</span><span class="sxs-lookup"><span data-stu-id="45d82-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="45d82-136">因此，不應該有轉換運算子來將轉換成 `Double(long)` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="45d82-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="45d82-137">在這種情況下，最好使用一個函式。</span><span class="sxs-lookup"><span data-stu-id="45d82-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="45d82-138">❌ 如果轉換可能失真，請勿提供隱含轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="45d82-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="45d82-139">例如，不應該從隱含轉換 `Double` 為， `Int32` 因為 `Double` 的範圍超出 `Int32` 。</span><span class="sxs-lookup"><span data-stu-id="45d82-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="45d82-140">即使轉換可能失真，也可以提供明確的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="45d82-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="45d82-141">❌ 請勿從隱含轉換擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="45d82-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="45d82-142">使用者很難瞭解發生什麼情況，因為他們可能不知道正在進行轉換。</span><span class="sxs-lookup"><span data-stu-id="45d82-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="45d82-143"><xref:System.InvalidCastException?displayProperty=nameWithType>如果對轉換運算子的呼叫導致失真轉換，而且運算子的合約不允許失真轉換，✔️會擲回。</span><span class="sxs-lookup"><span data-stu-id="45d82-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="45d82-144">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="45d82-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="45d82-145">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="45d82-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="45d82-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="45d82-146">See also</span></span>

- [<span data-ttu-id="45d82-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="45d82-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="45d82-148">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="45d82-148">Framework Design Guidelines</span></span>](index.md)
