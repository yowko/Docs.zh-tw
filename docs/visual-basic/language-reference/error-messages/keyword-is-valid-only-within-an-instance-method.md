---
title: "'<keyword>' 只能出現在執行個體方法中"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: ad39ade294b362b20f2dfb93455445bf41d056cd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163320"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="fedeb-102">BC30043： ' \<keyword> ' 只在實例方法內有效</span><span class="sxs-lookup"><span data-stu-id="fedeb-102">BC30043: '\<keyword>' is valid only within an instance method</span></span>

<span data-ttu-id="fedeb-103">`Me`、 `MyClass` 和關鍵字會 `MyBase` 參考特定的類別實例。</span><span class="sxs-lookup"><span data-stu-id="fedeb-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="fedeb-104">您無法在共用或程式中使用它們 `Function` `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="fedeb-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>

<span data-ttu-id="fedeb-105">*錯誤 ID：*\* BC30043</span><span class="sxs-lookup"><span data-stu-id="fedeb-105">*Error ID:*\* BC30043</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fedeb-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fedeb-106">To correct this error</span></span>

- <span data-ttu-id="fedeb-107">請從程式中移除關鍵字，或從程式 `Shared` 聲明中移除關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fedeb-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="fedeb-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fedeb-108">See also</span></span>

- [<span data-ttu-id="fedeb-109">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="fedeb-109">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="fedeb-110">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="fedeb-110">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="fedeb-111">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="fedeb-111">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
