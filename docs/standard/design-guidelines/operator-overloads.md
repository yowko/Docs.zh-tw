---
title: 運算子多載
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ca42d25a5f3456c6a10eff76d7015656322abae
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131243"
---
# <a name="operator-overloads"></a><span data-ttu-id="4ccd4-102">運算子多載</span><span class="sxs-lookup"><span data-stu-id="4ccd4-102">Operator Overloads</span></span>
<span data-ttu-id="4ccd4-103">運算子多載可讓顯示如同它們是內建語言基本類型的 framework 型別。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="4ccd4-104">雖然允許，而且在某些情況下很有用，應該小心使用運算子多載。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="4ccd4-105">有許多的案例中的運算子多載已被濫用，例如架構設計人員何時啟動的作業，應該是簡單的方法中使用運算子。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="4ccd4-106">下列指導方針可協助您決定何時以及如何使用運算子多載。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="4ccd4-107">**X AVOID** 運算子多載，除了定義應該像是基本 （內建） 類型的類型。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="4ccd4-108">**✓ CONSIDER** 應該像是基本類型的類型中定義運算子多載。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="4ccd4-109">例如，<xref:System.String?displayProperty=nameWithType>已經`operator==`和`operator!=`定義。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="4ccd4-110">**✓ DO** 運算子多載定義表示數字的結構中 (例如<xref:System.Decimal?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="4ccd4-111">**X DO NOT** 別出心裁時定義運算子多載。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="4ccd4-112">運算子多載是在其中顯而易見的是作業的結果將會的很有用。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="4ccd4-113">比方說，是合理能夠減一<xref:System.DateTime>從另一個`DateTime`，並取得<xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="4ccd4-114">不過，它不適合使用聯集的這兩個資料庫查詢的邏輯聯集運算子，或使用 shift 鍵運算子來寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="4ccd4-115">**X DO NOT** 提供運算子多載，除非其中至少一個運算元是定義多載的型別。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="4ccd4-116">**✓ DO** 對稱方式多載運算子。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="4ccd4-117">例如，如果您多載`operator==`，您也應該多載`operator!=`。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="4ccd4-118">同樣地，如果您多載`operator<`，您也應該多載`operator>`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="4ccd4-119">**✓ CONSIDER** 提供具有對應的好記名稱的方法與每個多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="4ccd4-120">許多語言不支援運算子多載。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="4ccd4-121">基於這個理由，建議您使用多載運算子的類型，包括第二種方法提供對等功能的適當定義域專屬名稱。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="4ccd4-122">下表包含運算子和對應的好記的方法名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="4ccd4-123">C# 運算子符號</span><span class="sxs-lookup"><span data-stu-id="4ccd4-123">C# Operator Symbol</span></span>|<span data-ttu-id="4ccd4-124">中繼資料名稱</span><span class="sxs-lookup"><span data-stu-id="4ccd4-124">Metadata Name</span></span>|<span data-ttu-id="4ccd4-125">易記名稱</span><span class="sxs-lookup"><span data-stu-id="4ccd4-125">Friendly Name</span></span>|  
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
  
### <a name="overloading-operator-"></a><span data-ttu-id="4ccd4-126">多載運算子 = =</span><span class="sxs-lookup"><span data-stu-id="4ccd4-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="4ccd4-127">多載`operator ==`是相當複雜。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="4ccd4-128">運算子的語意需要相容於數個其他的成員，例如<xref:System.Object.Equals%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="4ccd4-129">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="4ccd4-129">Conversion Operators</span></span>  
 <span data-ttu-id="4ccd4-130">轉換運算子是一元 （unary） 運算子，允許從一個類型轉換為另一個。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="4ccd4-131">運算子必須定義為運算元或傳回型別上的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="4ccd4-132">有兩種類型的轉換運算子： 隱含和明確。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="4ccd4-133">**X DO NOT** 提供轉換運算子，如果這類轉換不清楚所預期的使用者。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="4ccd4-134">**X DO NOT** 定義轉換運算子的型別網域之外。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="4ccd4-135">例如， <xref:System.Int32>， <xref:System.Double>，並<xref:System.Decimal>全部都是數值類型，而<xref:System.DateTime>不是。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="4ccd4-136">因此，應該會有任何要轉換的轉換運算子`Double(long)`至`DateTime`。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="4ccd4-137">建構函式是這種情況的慣用物件。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="4ccd4-138">**X DO NOT** 提供隱含轉換運算子，如果轉換可能會失真。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="4ccd4-139">比方說，不應該有的隱含轉換`Double`要`Int32`因為`Double`更廣的範圍，大於`Int32`。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="4ccd4-140">您可以提供明確轉換運算子，即使轉換可能會失真。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="4ccd4-141">**X DO NOT** 擲回例外狀況，從隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="4ccd4-142">它是很難了解發生什麼動作，因為它們可能不會察覺轉換正在進行中的使用者。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="4ccd4-143">**✓ DO** 擲回 <xref:System.InvalidCastException?displayProperty=nameWithType> 如果轉型運算子的呼叫會導致損失的轉換和運算子的合約不允許轉換損失。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="4ccd4-144">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="4ccd4-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4ccd4-145">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="4ccd4-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ccd4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ccd4-146">See also</span></span>

- [<span data-ttu-id="4ccd4-147">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="4ccd4-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="4ccd4-148">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="4ccd4-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
