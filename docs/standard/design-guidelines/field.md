---
title: 欄位設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 3ab8fe279605c4795bb3a26557d0241b186b273a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690445"
---
# <a name="field-design"></a><span data-ttu-id="acd58-102">欄位設計</span><span class="sxs-lookup"><span data-stu-id="acd58-102">Field Design</span></span>
<span data-ttu-id="acd58-103">封裝原則可讓其中一個最重要的概念是物件導向設計中。</span><span class="sxs-lookup"><span data-stu-id="acd58-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="acd58-104">此原則就是儲存在物件內的資料必須能夠存取只適用於該物件。</span><span class="sxs-lookup"><span data-stu-id="acd58-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="acd58-105">實用的方式來解譯原則是說應該設計為型別，以便可以對進行變更 （名稱或類型的變更） 該類型的欄位，而不會中斷程式碼以外之成員的型別。</span><span class="sxs-lookup"><span data-stu-id="acd58-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="acd58-106">此解譯立即表示所有欄位必須都是私用。</span><span class="sxs-lookup"><span data-stu-id="acd58-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="acd58-107">因為這類欄位中，幾乎是根據定義，永遠不需要變更，我們可以排除從這個嚴格限制的常數和靜態唯讀欄位。</span><span class="sxs-lookup"><span data-stu-id="acd58-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="acd58-108">**X DO NOT** 提供公用或受保護的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="acd58-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="acd58-109">您應該提供屬性存取欄位，而不是公用或受保護，請將它們。</span><span class="sxs-lookup"><span data-stu-id="acd58-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="acd58-110">**✓ DO** 常數欄位使用的常數，永遠不會變更。</span><span class="sxs-lookup"><span data-stu-id="acd58-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="acd58-111">編譯器會燒壞 const 欄位的值，直接在呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="acd58-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="acd58-112">因此，可以永遠不會變更常數的值，而不需要中斷相容性的風險。</span><span class="sxs-lookup"><span data-stu-id="acd58-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="acd58-113">**✓ DO** 使用公用靜態 `readonly` 預先定義的物件執行個體的欄位。</span><span class="sxs-lookup"><span data-stu-id="acd58-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="acd58-114">如果有預先定義的類型執行個體，請將它們宣告為公用唯讀靜態欄位的型別本身。</span><span class="sxs-lookup"><span data-stu-id="acd58-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="acd58-115">**X DO NOT** 指派到可變動類型的執行個體 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="acd58-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="acd58-116">可變動的型別是可以執行個體化之後進行修改的執行個體的類型。</span><span class="sxs-lookup"><span data-stu-id="acd58-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="acd58-117">例如，陣列、 大多數的集合和資料流是可變動的型別，但<xref:System.Int32?displayProperty=nameWithType>， <xref:System.Uri?displayProperty=nameWithType>，和<xref:System.String?displayProperty=nameWithType>全都是不變。</span><span class="sxs-lookup"><span data-stu-id="acd58-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="acd58-118">參考型別欄位上的唯讀修飾詞會防止執行個體儲存在欄位中，從已經被取代，但它無法防止呼叫成員變更的執行個體正在修改欄位的執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="acd58-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="acd58-119">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="acd58-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="acd58-120">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="acd58-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd58-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd58-121">See also</span></span>

- [<span data-ttu-id="acd58-122">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="acd58-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="acd58-123">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="acd58-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
