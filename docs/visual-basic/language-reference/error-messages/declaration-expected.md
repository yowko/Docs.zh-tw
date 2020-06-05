---
title: 必須是宣告
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 237622d0dc6c57f66d402f491a6191a5911574e2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409734"
---
# <a name="declaration-expected"></a><span data-ttu-id="9d462-102">必須是宣告</span><span class="sxs-lookup"><span data-stu-id="9d462-102">Declaration expected</span></span>
<span data-ttu-id="9d462-103">Nondeclarative 語句（例如指派或迴圈語句）會發生在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="9d462-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="9d462-104">在程式之外只允許宣告。</span><span class="sxs-lookup"><span data-stu-id="9d462-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="9d462-105">或者，在沒有宣告關鍵字（例如或）的情況下宣告程式設計項目 `Dim` `Const` 。</span><span class="sxs-lookup"><span data-stu-id="9d462-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="9d462-106">**錯誤識別碼：** BC30188</span><span class="sxs-lookup"><span data-stu-id="9d462-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d462-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9d462-107">To correct this error</span></span>  
  
- <span data-ttu-id="9d462-108">將 nondeclarative 語句移至程式的主體。</span><span class="sxs-lookup"><span data-stu-id="9d462-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
- <span data-ttu-id="9d462-109">使用適當的宣告關鍵字來開始宣告。</span><span class="sxs-lookup"><span data-stu-id="9d462-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
- <span data-ttu-id="9d462-110">請確定宣告關鍵字未拼錯。</span><span class="sxs-lookup"><span data-stu-id="9d462-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d462-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d462-111">See also</span></span>

- [<span data-ttu-id="9d462-112">程序</span><span class="sxs-lookup"><span data-stu-id="9d462-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="9d462-113">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="9d462-113">Dim Statement</span></span>](../statements/dim-statement.md)
