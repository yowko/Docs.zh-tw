---
title: 陳述式不能在 'If' 陳述式行之外結束區塊
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 4fd7577accd0b312ee1e3d2d990d256514d5f5f6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161331"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="560d8-102">BC32005：語句不能在 ' If ' 語句行之外結束區塊</span><span class="sxs-lookup"><span data-stu-id="560d8-102">BC32005: Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="560d8-103">單行 `If` 語句包含數個以冒號分隔的語句 (： ) ，其中一個語句是 `End` 單一行以外的控制項區塊語句 `If` 。</span><span class="sxs-lookup"><span data-stu-id="560d8-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="560d8-104">單行 `If` 語句不會使用 `End If` 語句。</span><span class="sxs-lookup"><span data-stu-id="560d8-104">Single-line `If` statements do not use the `End If` statement.</span></span>

 <span data-ttu-id="560d8-105">**錯誤識別碼：** BC32005</span><span class="sxs-lookup"><span data-stu-id="560d8-105">**Error ID:** BC32005</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="560d8-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="560d8-106">To correct this error</span></span>

- <span data-ttu-id="560d8-107">將單行語句移至 `If` 包含語句的控制項區塊外部 `End If` 。</span><span class="sxs-lookup"><span data-stu-id="560d8-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="560d8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="560d8-108">See also</span></span>

- [<span data-ttu-id="560d8-109">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="560d8-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
