---
title: Private Protected
ms.date: 05/10/2018
f1_keywords:
- vb.PrivateProtected
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 8ad1509da71bc80b33700d363ddd4569a0965dff
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303461"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="692f7-102">私用保護（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="692f7-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="692f7-103">`Private Protected` 關鍵字組合是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="692f7-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="692f7-104">`Private Protected`成員可由其包含類別中的所有成員，以及衍生自包含類別的類型來存取，但只有在其包含的元件中找到時才可以。</span><span class="sxs-lookup"><span data-stu-id="692f7-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="692f7-105">您 `Private Protected` 只能在類別的成員上指定，因為無法繼承結構，所以無法套用 `Private Protected` 到結構的成員。</span><span class="sxs-lookup"><span data-stu-id="692f7-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="692f7-106">`Private Protected`Visual Basic 15.5 和更新版本支援存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="692f7-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="692f7-107">若要使用它，您可以將下列元素加入至 Visual Basic 專案（ \* . vbproj）檔案。</span><span class="sxs-lookup"><span data-stu-id="692f7-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="692f7-108">只要您的系統上已安裝 Visual Basic 15.5 或更新版本，它就可讓您利用最新版本的 Visual Basic 編譯器所支援的所有語言功能：</span><span class="sxs-lookup"><span data-stu-id="692f7-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="692f7-109">如需詳細資訊，請參閱[設定 Visual Basic 語言版本](../configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="692f7-109">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="692f7-110">在 Visual Studio 中，選取 [F1 `private protected` 說明] 會提供[私](private.md)用[或受保護](protected.md)的協助。</span><span class="sxs-lookup"><span data-stu-id="692f7-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="692f7-111">IDE 會挑選游標下的單一 token，而不是複合字組。</span><span class="sxs-lookup"><span data-stu-id="692f7-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="692f7-112">規則</span><span class="sxs-lookup"><span data-stu-id="692f7-112">Rules</span></span>

- <span data-ttu-id="692f7-113">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="692f7-113">**Declaration Context.**</span></span> <span data-ttu-id="692f7-114">您 `Private Protected` 只能在類別層級使用。</span><span class="sxs-lookup"><span data-stu-id="692f7-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="692f7-115">這表示元素的宣告內容 `Protected` 必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。</span><span class="sxs-lookup"><span data-stu-id="692f7-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="692f7-116">行為</span><span class="sxs-lookup"><span data-stu-id="692f7-116">Behavior</span></span>

- <span data-ttu-id="692f7-117">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="692f7-117">**Access Level.**</span></span> <span data-ttu-id="692f7-118">類別中的所有程式碼都可以存取其元素。</span><span class="sxs-lookup"><span data-stu-id="692f7-118">All code in a class can access its elements.</span></span> <span data-ttu-id="692f7-119">任何衍生自基類且包含在相同元件中的類別中的程式碼，都可以存取基類的所有 `Private Protected` 元素。</span><span class="sxs-lookup"><span data-stu-id="692f7-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="692f7-120">不過，任何衍生自基類且包含在不同元件中的類別中的程式碼，都無法存取基類 `Private Protected` 元素。</span><span class="sxs-lookup"><span data-stu-id="692f7-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="692f7-121">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="692f7-121">**Access Modifiers.**</span></span> <span data-ttu-id="692f7-122">指定存取層級的關鍵字稱為*存取*修飾詞。</span><span class="sxs-lookup"><span data-stu-id="692f7-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="692f7-123">如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="692f7-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="692f7-124">`Private Protected` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="692f7-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="692f7-125">Nested 類別的[Class 語句](../statements/class-statement.md)</span><span class="sxs-lookup"><span data-stu-id="692f7-125">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="692f7-126">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="692f7-126">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="692f7-127">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="692f7-127">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="692f7-128">在類別中嵌套之委派的[委派語句](../statements/delegate-statement.md)</span><span class="sxs-lookup"><span data-stu-id="692f7-128">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="692f7-129">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="692f7-129">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="692f7-130">在類別中嵌套之列舉的[Enum 語句](../statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="692f7-130">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="692f7-131">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="692f7-131">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="692f7-132">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="692f7-132">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="692f7-133">類別中所嵌套介面的[介面語句](../statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="692f7-133">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="692f7-134">Property Statement</span><span class="sxs-lookup"><span data-stu-id="692f7-134">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="692f7-135">類別中所嵌套結構的[結構語句](../statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="692f7-135">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="692f7-136">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="692f7-136">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="692f7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="692f7-137">See also</span></span>

- [<span data-ttu-id="692f7-138">公開</span><span class="sxs-lookup"><span data-stu-id="692f7-138">Public</span></span>](public.md)
- [<span data-ttu-id="692f7-139">免受</span><span class="sxs-lookup"><span data-stu-id="692f7-139">Protected</span></span>](protected.md)
- [<span data-ttu-id="692f7-140">給</span><span class="sxs-lookup"><span data-stu-id="692f7-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="692f7-141">私用</span><span class="sxs-lookup"><span data-stu-id="692f7-141">Private</span></span>](private.md)
- [<span data-ttu-id="692f7-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="692f7-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="692f7-143">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="692f7-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="692f7-144">程序</span><span class="sxs-lookup"><span data-stu-id="692f7-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="692f7-145">結構</span><span class="sxs-lookup"><span data-stu-id="692f7-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="692f7-146">物件和類別</span><span class="sxs-lookup"><span data-stu-id="692f7-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
