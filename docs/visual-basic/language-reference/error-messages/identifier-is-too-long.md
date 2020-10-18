---
title: 識別項太長
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: eafcb2fdf706e12fa606a442ad577c88ed5a7427
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162852"
---
# <a name="bc30033-identifier-is-too-long"></a><span data-ttu-id="e69bd-102">BC30033：識別碼太長</span><span class="sxs-lookup"><span data-stu-id="e69bd-102">BC30033: Identifier is too long</span></span>

<span data-ttu-id="e69bd-103">每個程式設計項目的名稱或識別碼限制為1023個字元。</span><span class="sxs-lookup"><span data-stu-id="e69bd-103">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="e69bd-104">此外，完整名稱不能超過1023個字元。</span><span class="sxs-lookup"><span data-stu-id="e69bd-104">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="e69bd-105">這表示 () 的整個識別碼字串 `<namespace>.<...>.<namespace>.<class>.<element>` 長度不能超過1023個字元，包括成員存取運算子 (`.`) 個字元。</span><span class="sxs-lookup"><span data-stu-id="e69bd-105">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>

 <span data-ttu-id="e69bd-106">**錯誤識別碼：** BC30033</span><span class="sxs-lookup"><span data-stu-id="e69bd-106">**Error ID:** BC30033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e69bd-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e69bd-107">To correct this error</span></span>

- <span data-ttu-id="e69bd-108">減少識別項的長度。</span><span class="sxs-lookup"><span data-stu-id="e69bd-108">Reduce the length of the identifier.</span></span>

## <a name="see-also"></a><span data-ttu-id="e69bd-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e69bd-109">See also</span></span>

- [<span data-ttu-id="e69bd-110">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="e69bd-110">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
