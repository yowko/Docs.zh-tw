---
title: 必須是宣告
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 2755f5afcb96ca7a6c4d140908649390dd66d571
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162696"
---
# <a name="bc30188-declaration-expected"></a><span data-ttu-id="cdda6-102">BC30188：需要宣告</span><span class="sxs-lookup"><span data-stu-id="cdda6-102">BC30188: Declaration expected</span></span>

<span data-ttu-id="cdda6-103">Nondeclarative 語句（例如指派或迴圈語句）發生在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="cdda6-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="cdda6-104">在程式之外只允許宣告。</span><span class="sxs-lookup"><span data-stu-id="cdda6-104">Only declarations are allowed outside procedures.</span></span>

 <span data-ttu-id="cdda6-105">或者，在不使用宣告關鍵字（例如或）的情況下宣告程式設計項目 `Dim` `Const` 。</span><span class="sxs-lookup"><span data-stu-id="cdda6-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>

 <span data-ttu-id="cdda6-106">**錯誤識別碼：** BC30188</span><span class="sxs-lookup"><span data-stu-id="cdda6-106">**Error ID:** BC30188</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cdda6-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cdda6-107">To correct this error</span></span>

- <span data-ttu-id="cdda6-108">將 nondeclarative 語句移至程式的主體。</span><span class="sxs-lookup"><span data-stu-id="cdda6-108">Move the nondeclarative statement to the body of a procedure.</span></span>

- <span data-ttu-id="cdda6-109">使用適當的宣告關鍵字來開始宣告。</span><span class="sxs-lookup"><span data-stu-id="cdda6-109">Begin the declaration with an appropriate declaration keyword.</span></span>

- <span data-ttu-id="cdda6-110">確定宣告關鍵字未拼寫錯誤。</span><span class="sxs-lookup"><span data-stu-id="cdda6-110">Ensure that a declaration keyword is not misspelled.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdda6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdda6-111">See also</span></span>

- [<span data-ttu-id="cdda6-112">程序</span><span class="sxs-lookup"><span data-stu-id="cdda6-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="cdda6-113">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="cdda6-113">Dim Statement</span></span>](../statements/dim-statement.md)
