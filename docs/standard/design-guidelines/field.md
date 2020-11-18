---
title: 欄位設計
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 6e58274f32ea129d3271c11e321bdbd454d2406a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821108"
---
# <a name="field-design"></a><span data-ttu-id="95e22-102">欄位設計</span><span class="sxs-lookup"><span data-stu-id="95e22-102">Field Design</span></span>
<span data-ttu-id="95e22-103">封裝的原則是物件導向設計中最重要的觀念之一。</span><span class="sxs-lookup"><span data-stu-id="95e22-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="95e22-104">這項原則指出，儲存在物件內的資料只能供該物件存取。</span><span class="sxs-lookup"><span data-stu-id="95e22-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="95e22-105">解讀原則的一個實用方式是說，您應該設計一個型別，讓該類型的欄位變更 (名稱或類型) 變更，而不需要中斷任何程式碼，而不是類型的成員。</span><span class="sxs-lookup"><span data-stu-id="95e22-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="95e22-106">這種轉譯會立即暗示所有欄位都必須是私用的。</span><span class="sxs-lookup"><span data-stu-id="95e22-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="95e22-107">我們會從這項嚴格的限制中排除常數和靜態唯讀欄位，因為這類欄位幾乎都是由定義所變更。</span><span class="sxs-lookup"><span data-stu-id="95e22-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="95e22-108">❌ 請勿提供公用或受保護的實例欄位。</span><span class="sxs-lookup"><span data-stu-id="95e22-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="95e22-109">您應該提供屬性來存取欄位，而不是將它們設為公用或受保護。</span><span class="sxs-lookup"><span data-stu-id="95e22-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="95e22-110">✔️針對永遠不會變更的常數，請使用常數位段。</span><span class="sxs-lookup"><span data-stu-id="95e22-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="95e22-111">編譯器會將 const 欄位的值直接燒錄到呼叫程式碼中。</span><span class="sxs-lookup"><span data-stu-id="95e22-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="95e22-112">因此，若沒有中斷相容性的風險，就永遠無法變更 const 值。</span><span class="sxs-lookup"><span data-stu-id="95e22-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="95e22-113">✔️使用 `readonly` 預先定義之物件實例的公用靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="95e22-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="95e22-114">如果有預先定義的類型實例，請將其宣告為類型本身的公用唯讀靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="95e22-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="95e22-115">❌ 請勿將可變類型的實例指派給 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="95e22-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="95e22-116">可變動型別是一種類型，具有可在具現化之後修改的實例。</span><span class="sxs-lookup"><span data-stu-id="95e22-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="95e22-117">例如，陣列、大部分的集合和資料流程都是可變動的類型，但 <xref:System.Int32?displayProperty=nameWithType> 、 <xref:System.Uri?displayProperty=nameWithType> 和 <xref:System.String?displayProperty=nameWithType> 都是不可變的。</span><span class="sxs-lookup"><span data-stu-id="95e22-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="95e22-118">參考型別字段上的唯讀修飾詞可防止取代儲存在欄位中的實例，但是它不會藉由呼叫成員來變更實例來防止修改欄位的實例資料。</span><span class="sxs-lookup"><span data-stu-id="95e22-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="95e22-119">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="95e22-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="95e22-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="95e22-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="95e22-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="95e22-121">See also</span></span>

- [<span data-ttu-id="95e22-122">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="95e22-122">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="95e22-123">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="95e22-123">Framework Design Guidelines</span></span>](index.md)
