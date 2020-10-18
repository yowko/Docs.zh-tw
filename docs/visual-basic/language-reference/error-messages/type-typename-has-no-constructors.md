---
title: 類型 '<typename>' 沒有建構函式
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 249bcb7020f26c7c43d560e91ef7a34e4dc64470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161175"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="648eb-102">BC30251：類型 ' \<typename> ' 沒有任何函數</span><span class="sxs-lookup"><span data-stu-id="648eb-102">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="648eb-103">類型不支援呼叫 `Sub New()`。</span><span class="sxs-lookup"><span data-stu-id="648eb-103">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="648eb-104">一個可能原因是編譯器或二進位檔案損毀。</span><span class="sxs-lookup"><span data-stu-id="648eb-104">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="648eb-105">**錯誤識別碼：** BC30251</span><span class="sxs-lookup"><span data-stu-id="648eb-105">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="648eb-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="648eb-106">To correct this error</span></span>

1. <span data-ttu-id="648eb-107">如果類型是在不同專案中，或是在參考的檔案中，請重新安裝專案或檔案。</span><span class="sxs-lookup"><span data-stu-id="648eb-107">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="648eb-108">如果類型是在相同專案中，請重新編譯包含類型的組件。</span><span class="sxs-lookup"><span data-stu-id="648eb-108">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="648eb-109">如果錯誤重複發生，請重新安裝 Visual Basic 編譯器。</span><span class="sxs-lookup"><span data-stu-id="648eb-109">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="648eb-110">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="648eb-110">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="648eb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="648eb-111">See also</span></span>

- [<span data-ttu-id="648eb-112">物件和類別</span><span class="sxs-lookup"><span data-stu-id="648eb-112">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="648eb-113">與我們交談</span><span class="sxs-lookup"><span data-stu-id="648eb-113">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
