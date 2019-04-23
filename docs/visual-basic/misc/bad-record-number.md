---
title: 不正確的資料錄數目
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: abd0a1467c0991a40b93e74a1d7a7889367fb8ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340798"
---
# <a name="bad-record-number"></a><span data-ttu-id="b7a3b-102">不正確的資料錄數目</span><span class="sxs-lookup"><span data-stu-id="b7a3b-102">Bad record number</span></span>
<span data-ttu-id="b7a3b-103">`a FileGet`、 `FilePut`、 `FileGetObject`或 `FilePutObject` 陳述式中的資料錄數目小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="b7a3b-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7a3b-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b7a3b-104">To correct this error</span></span>  
  
1. <span data-ttu-id="b7a3b-105">檢查用於產生資料錄數目的計算。</span><span class="sxs-lookup"><span data-stu-id="b7a3b-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="b7a3b-106">確認包含資料錄數目或用於計算資料錄數目的變數拼字正確。</span><span class="sxs-lookup"><span data-stu-id="b7a3b-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="b7a3b-107">除非在模組中使用 `Option Explicit On` ，否則拼錯的變數名稱會隱含宣告並初始化為零。</span><span class="sxs-lookup"><span data-stu-id="b7a3b-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a3b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7a3b-108">See also</span></span>

- [<span data-ttu-id="b7a3b-109">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="b7a3b-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
