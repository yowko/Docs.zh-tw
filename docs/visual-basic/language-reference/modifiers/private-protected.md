---
title: Private Protected (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: fea43558ac0fe8181f2786b69f2621346d446b2e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376386"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="05ff4-102">Private Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05ff4-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="05ff4-103">`Private Protected` 關鍵字組合是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="05ff4-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="05ff4-104">A`Private Protected`成員是其包含的類別中的所有成員，以及衍生自包含類別，型別，可供存取，但前提是其包含的組件中找到。</span><span class="sxs-lookup"><span data-stu-id="05ff4-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="05ff4-105">您可以指定`Private Protected`只能在類別; 的成員上不能套用`Private Protected`的結構成員因為結構無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="05ff4-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="05ff4-106">`Private Protected` Visual Basic 15.5 和更新版本支援的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="05ff4-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="05ff4-107">若要使用它，您可以將下列項目新增至 Visual Basic 專案 (\*.vbproj) 檔案。</span><span class="sxs-lookup"><span data-stu-id="05ff4-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="05ff4-108">只要 Visual Basic 15.5 或更新版本安裝在您的系統上，它可讓您充分利用所有最新版本的 Visual Basic 編譯器所支援的語言功能：</span><span class="sxs-lookup"><span data-stu-id="05ff4-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="05ff4-109">如需詳細資訊，請參閱[設定的 Visual Basic 語言版本](../../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="05ff4-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="05ff4-110">在 Visual Studio 中，選取 上的 F1 說明`private protected`提供的其中一個 說明[私人](private.md)或是[保護](protected.md)。</span><span class="sxs-lookup"><span data-stu-id="05ff4-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="05ff4-111">IDE 會挑選單一語彙基元，在資料指標，而不是複合字。</span><span class="sxs-lookup"><span data-stu-id="05ff4-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="05ff4-112">規則</span><span class="sxs-lookup"><span data-stu-id="05ff4-112">Rules</span></span>

- <span data-ttu-id="05ff4-113">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="05ff4-113">**Declaration Context.**</span></span> <span data-ttu-id="05ff4-114">您可以使用`Private Protected`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="05ff4-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="05ff4-115">這表示的宣告內容`Protected`項目必須是類別，，而且不能是原始程式檔、 命名空間、 介面、 模組、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="05ff4-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="05ff4-116">行為</span><span class="sxs-lookup"><span data-stu-id="05ff4-116">Behavior</span></span>

- <span data-ttu-id="05ff4-117">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="05ff4-117">**Access Level.**</span></span> <span data-ttu-id="05ff4-118">在類別中的所有程式碼可以存取其項目。</span><span class="sxs-lookup"><span data-stu-id="05ff4-118">All code in a class can access its elements.</span></span> <span data-ttu-id="05ff4-119">在任何類別都衍生自基底類別，而且會包含在相同的組件中的程式碼可以存取所有`Private Protected`基底類別的項目。</span><span class="sxs-lookup"><span data-stu-id="05ff4-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="05ff4-120">不過，任何類別都衍生自基底類別，而且會包含在不同的組件中的程式碼無法存取的基底類別`Private Protected`項目。</span><span class="sxs-lookup"><span data-stu-id="05ff4-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="05ff4-121">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="05ff4-121">**Access Modifiers.**</span></span> <span data-ttu-id="05ff4-122">指定存取層級的關鍵字稱為*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="05ff4-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="05ff4-123">如需存取修飾詞的比較，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="05ff4-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="05ff4-124">
  `Private Protected\` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="05ff4-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="05ff4-125">[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)的巢狀類別</span><span class="sxs-lookup"><span data-stu-id="05ff4-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="05ff4-126">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="05ff4-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="05ff4-127">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="05ff4-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- <span data-ttu-id="05ff4-128">[Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)委派的巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="05ff4-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="05ff4-129">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="05ff4-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- <span data-ttu-id="05ff4-130">[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)列舉型別的巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="05ff4-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="05ff4-131">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="05ff4-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="05ff4-132">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="05ff4-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- <span data-ttu-id="05ff4-133">[Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)介面的巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="05ff4-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="05ff4-134">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="05ff4-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- <span data-ttu-id="05ff4-135">[結構，陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)結構的巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="05ff4-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="05ff4-136">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="05ff4-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="05ff4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05ff4-137">See also</span></span>

- [<span data-ttu-id="05ff4-138">Public</span><span class="sxs-lookup"><span data-stu-id="05ff4-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="05ff4-139">Protected</span><span class="sxs-lookup"><span data-stu-id="05ff4-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="05ff4-140">Friend</span><span class="sxs-lookup"><span data-stu-id="05ff4-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="05ff4-141">Private</span><span class="sxs-lookup"><span data-stu-id="05ff4-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="05ff4-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="05ff4-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="05ff4-143">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="05ff4-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="05ff4-144">程序</span><span class="sxs-lookup"><span data-stu-id="05ff4-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="05ff4-145">結構</span><span class="sxs-lookup"><span data-stu-id="05ff4-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="05ff4-146">物件和類別</span><span class="sxs-lookup"><span data-stu-id="05ff4-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
