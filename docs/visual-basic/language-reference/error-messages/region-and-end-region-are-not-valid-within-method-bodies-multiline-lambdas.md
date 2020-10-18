---
title: "'#Region' 與 ' #End Region' 陳述式在具有多行的方法主體中無效"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c792fa1a42bde22959ae21439cb2a0a1e4be343f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162280"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="02fc2-102">BC32025： ' #Region ' 和 ' #End Region ' 語句在方法主體/多行 lambda 中無效</span><span class="sxs-lookup"><span data-stu-id="02fc2-102">BC32025: '#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="02fc2-103">`#Region`區塊必須在類別、模組或命名空間層級進行宣告。</span><span class="sxs-lookup"><span data-stu-id="02fc2-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="02fc2-104">可折迭的區域可以包含一或多個程式，但它不能在程式內開始或結束。</span><span class="sxs-lookup"><span data-stu-id="02fc2-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>

 <span data-ttu-id="02fc2-105">**錯誤識別碼：** BC32025</span><span class="sxs-lookup"><span data-stu-id="02fc2-105">**Error ID:** BC32025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="02fc2-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="02fc2-106">To correct this error</span></span>

1. <span data-ttu-id="02fc2-107">請確定先前的程式已使用或語句正確地終止 `End Function` `End Sub` 。</span><span class="sxs-lookup"><span data-stu-id="02fc2-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="02fc2-108">確定和指示詞位於 `#Region` `#End Region` 相同的程式碼區塊中。</span><span class="sxs-lookup"><span data-stu-id="02fc2-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>

## <a name="see-also"></a><span data-ttu-id="02fc2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02fc2-109">See also</span></span>

- [<span data-ttu-id="02fc2-110">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="02fc2-110">#Region Directive</span></span>](../directives/region-directive.md)
