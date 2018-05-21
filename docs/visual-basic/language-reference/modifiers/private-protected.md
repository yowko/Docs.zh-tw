---
title: 私用受保護的 (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="3e7d7-102">私用受保護的 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e7d7-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="3e7d7-103">`Private Protected`關鍵字的組合都是成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="3e7d7-104">A`Private Protected`成員是可存取它的包含類別中的所有成員，以及衍生自包含類別，但前提是其包含的組件中找到。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="3e7d7-105">您可以指定`Private Protected`只成員上的類別; 無法套用`Private Protected`結構的成員因為結構無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="3e7d7-106">`Private Protected`存取修飾詞支援的 Visual Basic 15.5 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="3e7d7-107">若要使用它，您可以將下列項目加入 Visual Basic 專案 (\*.vbproj) 檔。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="3e7d7-108">只要 Visual Basic 15.5 或更新版本安裝在您的系統上，它可讓您充分利用所有最新版本的 Visual Basic 編譯器所支援的語言功能：</span><span class="sxs-lookup"><span data-stu-id="3e7d7-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="3e7d7-109">在 Visual Studio 中，選取 F1 說明上`private protected`提供任何說明[私人](private.md)或[保護](protected.md)。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-109">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="3e7d7-110">IDE 會挑選單一語彙基元，在資料指標，而不是複合字。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-110">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="3e7d7-111">規則</span><span class="sxs-lookup"><span data-stu-id="3e7d7-111">Rules</span></span>

- <span data-ttu-id="3e7d7-112">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="3e7d7-112">**Declaration Context.**</span></span> <span data-ttu-id="3e7d7-113">您可以使用`Private Protected`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-113">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="3e7d7-114">這表示宣告內容`Protected`項目必須是類別，且不能原始程式檔、 命名空間、 介面、 模組、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-114">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="3e7d7-115">行為</span><span class="sxs-lookup"><span data-stu-id="3e7d7-115">Behavior</span></span>

- <span data-ttu-id="3e7d7-116">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="3e7d7-116">**Access Level.**</span></span> <span data-ttu-id="3e7d7-117">類別中的所有程式碼可以存取其項目。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-117">All code in a class can access its elements.</span></span> <span data-ttu-id="3e7d7-118">任何衍生自基底類別，而且會包含在相同的組件的類別中的程式碼可以存取所有`Private Protected`基底類別的項目。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-118">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="3e7d7-119">不過，在任何類別，衍生自基底類別，而且會包含在不同的組件中的程式碼無法存取基底類別`Private Protected`項目。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-119">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="3e7d7-120">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="3e7d7-120">**Access Modifiers.**</span></span> <span data-ttu-id="3e7d7-121">指定存取層級的關鍵字稱為*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-121">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="3e7d7-122">如需存取修飾詞的比較，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3e7d7-122">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="3e7d7-123">`Private Protected` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="3e7d7-123">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="3e7d7-124">[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)的巢狀類別</span><span class="sxs-lookup"><span data-stu-id="3e7d7-124">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="3e7d7-125">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e7d7-125">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="3e7d7-126">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e7d7-126">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="3e7d7-127">[Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)委派的巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="3e7d7-127">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="3e7d7-128">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e7d7-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="3e7d7-129">[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)eumeration 巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="3e7d7-129">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="3e7d7-130">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e7d7-130">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="3e7d7-131">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e7d7-131">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="3e7d7-132">[Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)介面的巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="3e7d7-132">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="3e7d7-133">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e7d7-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="3e7d7-134">[結構陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)結構的巢狀類別中</span><span class="sxs-lookup"><span data-stu-id="3e7d7-134">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="3e7d7-135">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e7d7-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e7d7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e7d7-136">See Also</span></span>

[<span data-ttu-id="3e7d7-137">Public</span><span class="sxs-lookup"><span data-stu-id="3e7d7-137">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="3e7d7-138">Protected</span><span class="sxs-lookup"><span data-stu-id="3e7d7-138">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="3e7d7-139">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="3e7d7-139">[Friend](friend.md) </span></span>  
[<span data-ttu-id="3e7d7-140">Private</span><span class="sxs-lookup"><span data-stu-id="3e7d7-140">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="3e7d7-141">[Protected 的 Friend](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="3e7d7-141">[Protected Friend](./protected-friend.md) </span></span>  
[<span data-ttu-id="3e7d7-142">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="3e7d7-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="3e7d7-143">程序</span><span class="sxs-lookup"><span data-stu-id="3e7d7-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="3e7d7-144">結構</span><span class="sxs-lookup"><span data-stu-id="3e7d7-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="3e7d7-145">物件和類別</span><span class="sxs-lookup"><span data-stu-id="3e7d7-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
