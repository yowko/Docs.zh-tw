---
title: Imports '<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409461"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="eaa90-102">Imports '\<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型</span><span class="sxs-lookup"><span data-stu-id="eaa90-102">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="eaa90-103">匯入 ' ' 中指定的命名空間或類型 \<qualifiedelementname> 不包含任何 public 成員，或找不到。</span><span class="sxs-lookup"><span data-stu-id="eaa90-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="eaa90-104">請確定已定義命名空間或類型，而且包含至少一個公用成員。</span><span class="sxs-lookup"><span data-stu-id="eaa90-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="eaa90-105">請確定別名名稱不包含其他別名。</span><span class="sxs-lookup"><span data-stu-id="eaa90-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="eaa90-106">`Imports`語句指定了找不到或未定義任何成員的包含元素 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="eaa90-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="eaa90-107">*包含元素*可以是命名空間、類別、結構、模組、介面或列舉。</span><span class="sxs-lookup"><span data-stu-id="eaa90-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="eaa90-108">包含的元素包含成員，例如變數、程式或其他包含專案。</span><span class="sxs-lookup"><span data-stu-id="eaa90-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="eaa90-109">匯入的目的是要讓您的程式碼可以存取命名空間或類型成員，而不需要限定它們。</span><span class="sxs-lookup"><span data-stu-id="eaa90-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="eaa90-110">您的專案可能也需要加入命名空間或類型的參考。</span><span class="sxs-lookup"><span data-stu-id="eaa90-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="eaa90-111">如需詳細資訊，請參閱宣告專案[參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「匯入包含元素」。</span><span class="sxs-lookup"><span data-stu-id="eaa90-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="eaa90-112">如果編譯器找不到指定的包含元素，就無法解析使用它的參考。</span><span class="sxs-lookup"><span data-stu-id="eaa90-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="eaa90-113">如果找到專案，但元素並未公開任何 `Public` 成員，則不會有任何參考成功。</span><span class="sxs-lookup"><span data-stu-id="eaa90-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="eaa90-114">在任一情況下，匯入元素都沒有意義。</span><span class="sxs-lookup"><span data-stu-id="eaa90-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="eaa90-115">請記住，如果您匯入包含專案，並為其指派匯入別名，則無法使用該匯入別名來匯入另一個元素。</span><span class="sxs-lookup"><span data-stu-id="eaa90-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="eaa90-116">下列程式碼會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="eaa90-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="eaa90-117">**錯誤識別碼：** BC40056</span><span class="sxs-lookup"><span data-stu-id="eaa90-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eaa90-118">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="eaa90-118">To correct this error</span></span>

1. <span data-ttu-id="eaa90-119">確認可從您的專案存取包含的元素。</span><span class="sxs-lookup"><span data-stu-id="eaa90-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="eaa90-120">確認包含元素的規格不包含來自另一個匯入的任何匯入別名。</span><span class="sxs-lookup"><span data-stu-id="eaa90-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="eaa90-121">請確認包含的元素至少會公開一個 `Public` 成員。</span><span class="sxs-lookup"><span data-stu-id="eaa90-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="eaa90-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaa90-122">See also</span></span>

- [<span data-ttu-id="eaa90-123">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="eaa90-123">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="eaa90-124">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="eaa90-124">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="eaa90-125">公開</span><span class="sxs-lookup"><span data-stu-id="eaa90-125">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="eaa90-126">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="eaa90-126">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="eaa90-127">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="eaa90-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
