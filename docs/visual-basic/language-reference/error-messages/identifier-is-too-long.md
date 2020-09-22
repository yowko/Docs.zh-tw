---
title: 識別項太長
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: 084e3d9306ad84d7e6e36e5fe4bbfc868b8dfac6
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874003"
---
# <a name="identifier-is-too-long"></a><span data-ttu-id="bc194-102">識別項太長</span><span class="sxs-lookup"><span data-stu-id="bc194-102">Identifier is too long</span></span>

<span data-ttu-id="bc194-103">每個程式設計項目的名稱或識別碼限制為1023個字元。</span><span class="sxs-lookup"><span data-stu-id="bc194-103">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="bc194-104">此外，完整名稱不能超過1023個字元。</span><span class="sxs-lookup"><span data-stu-id="bc194-104">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="bc194-105">這表示 () 的整個識別碼字串 `<namespace>.<...>.<namespace>.<class>.<element>` 長度不能超過1023個字元，包括成員存取運算子 (`.`) 個字元。</span><span class="sxs-lookup"><span data-stu-id="bc194-105">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>  
  
 <span data-ttu-id="bc194-106">**錯誤識別碼：** BC30033</span><span class="sxs-lookup"><span data-stu-id="bc194-106">**Error ID:** BC30033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc194-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bc194-107">To correct this error</span></span>  
  
- <span data-ttu-id="bc194-108">減少識別項的長度。</span><span class="sxs-lookup"><span data-stu-id="bc194-108">Reduce the length of the identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc194-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc194-109">See also</span></span>

- [<span data-ttu-id="bc194-110">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="bc194-110">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
