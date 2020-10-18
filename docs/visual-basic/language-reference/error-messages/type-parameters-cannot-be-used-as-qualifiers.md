---
title: 類型參數不能當做限定詞使用
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 14e6094b0cc129eba86db1808c0f0575955f5e75
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161188"
---
# <a name="bc32098-type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="54fa7-102">BC32098：類型參數不能當做限定詞使用</span><span class="sxs-lookup"><span data-stu-id="54fa7-102">BC32098: Type parameters cannot be used as qualifiers</span></span>

<span data-ttu-id="54fa7-103">程式設計專案會以包含型別參數的限定性字串限定。</span><span class="sxs-lookup"><span data-stu-id="54fa7-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>

<span data-ttu-id="54fa7-104">型別參數代表在建立泛型型別時所要提供的型別需求。</span><span class="sxs-lookup"><span data-stu-id="54fa7-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="54fa7-105">它不代表特定的定義型別。</span><span class="sxs-lookup"><span data-stu-id="54fa7-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="54fa7-106">限定性字串只能包含編譯時期所定義的元素。</span><span class="sxs-lookup"><span data-stu-id="54fa7-106">A qualification string must include only elements that are defined at compile time.</span></span>

<span data-ttu-id="54fa7-107">下列程式碼可能會產生此錯誤：</span><span class="sxs-lookup"><span data-stu-id="54fa7-107">The following code can generate this error:</span></span>

```vb
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean

    Dim saveText As c.Text
    ' Insert code to look for badText within saveText.
End Function
```

 <span data-ttu-id="54fa7-108">**錯誤識別碼：** BC32098</span><span class="sxs-lookup"><span data-stu-id="54fa7-108">**Error ID:** BC32098</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="54fa7-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="54fa7-109">To correct this error</span></span>

1. <span data-ttu-id="54fa7-110">請從限定性字串中移除類型參數，或將它取代為已定義的類型。</span><span class="sxs-lookup"><span data-stu-id="54fa7-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>

2. <span data-ttu-id="54fa7-111">如果您需要使用結構化的型別來找出要限定的程式設計項目，您必須使用其他程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="54fa7-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>

## <a name="see-also"></a><span data-ttu-id="54fa7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54fa7-112">See also</span></span>

- [<span data-ttu-id="54fa7-113">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="54fa7-113">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="54fa7-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54fa7-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="54fa7-115">Type List</span><span class="sxs-lookup"><span data-stu-id="54fa7-115">Type List</span></span>](../statements/type-list.md)
