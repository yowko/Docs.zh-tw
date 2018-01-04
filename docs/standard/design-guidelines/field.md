---
title: "欄位設計"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ccced2c9e816122d770f43056c36ab4a6d510fde
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="field-design"></a><span data-ttu-id="b5fee-102">欄位設計</span><span class="sxs-lookup"><span data-stu-id="b5fee-102">Field Design</span></span>
<span data-ttu-id="b5fee-103">封裝 （encapsulation） 的原則就是其中一個最重要的概念在物件導向設計。</span><span class="sxs-lookup"><span data-stu-id="b5fee-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="b5fee-104">此原則就是儲存在物件內的資料必須能夠存取只適用於該物件。</span><span class="sxs-lookup"><span data-stu-id="b5fee-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="b5fee-105">實用的方式來解譯原則是說出應該設計為型別，使到該類型 （名稱或型別變更） 的欄位才能進行變更而不會中斷以外的程式碼類型的成員。</span><span class="sxs-lookup"><span data-stu-id="b5fee-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="b5fee-106">此解譯立即意味著所有欄位必須都是私用。</span><span class="sxs-lookup"><span data-stu-id="b5fee-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="b5fee-107">因為這類欄位，根據定義，幾乎永遠不需要變更，我們可以排除這個嚴格限制，從的常數和靜態唯讀欄位。</span><span class="sxs-lookup"><span data-stu-id="b5fee-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="b5fee-108">**X 不**提供公用或受保護的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="b5fee-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="b5fee-109">您應該提供屬性存取欄位，而不是公用或受保護，讓它們。</span><span class="sxs-lookup"><span data-stu-id="b5fee-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="b5fee-110">**✓ 不要**常數欄位使用的常數，永遠不會變更。</span><span class="sxs-lookup"><span data-stu-id="b5fee-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="b5fee-111">編譯器會直接將呼叫程式碼的 const 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b5fee-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="b5fee-112">因此，const 值永遠不會不會中斷相容性的變更。</span><span class="sxs-lookup"><span data-stu-id="b5fee-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="b5fee-113">**✓ 不要**使用公用靜態`readonly`預先定義的物件執行個體的欄位。</span><span class="sxs-lookup"><span data-stu-id="b5fee-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="b5fee-114">如果沒有預先定義的類型執行個體，請將其宣告為公用唯讀靜態欄位的型別本身。</span><span class="sxs-lookup"><span data-stu-id="b5fee-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="b5fee-115">**X 不**指派到可變動類型的執行個體`readonly`欄位。</span><span class="sxs-lookup"><span data-stu-id="b5fee-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="b5fee-116">可變動類型是具現化之後可修改的執行個體的類型。</span><span class="sxs-lookup"><span data-stu-id="b5fee-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="b5fee-117">例如，陣列中，大多數集合而言和資料流是可變動的型別，但<xref:System.Int32?displayProperty=nameWithType>， <xref:System.Uri?displayProperty=nameWithType>，和<xref:System.String?displayProperty=nameWithType>全都是不變。</span><span class="sxs-lookup"><span data-stu-id="b5fee-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="b5fee-118">上的參考類型欄位的唯讀修飾詞可避免被取代的欄位中儲存的執行個體，但它不會防止欄位的執行個體資料變更的執行個體的呼叫成員被修改。</span><span class="sxs-lookup"><span data-stu-id="b5fee-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="b5fee-119">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b5fee-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b5fee-120">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="b5fee-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fee-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5fee-121">See Also</span></span>  
 [<span data-ttu-id="b5fee-122">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="b5fee-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="b5fee-123">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b5fee-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
