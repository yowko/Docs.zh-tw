---
title: 必須是宣告
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 64ee75c93615f57b15fea29f06fff500a395ba0c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834175"
---
# <a name="declaration-expected"></a><span data-ttu-id="5205f-102">必須是宣告</span><span class="sxs-lookup"><span data-stu-id="5205f-102">Declaration expected</span></span>
<span data-ttu-id="5205f-103">非宣告陳述式，例如指派或迴圈陳述式，就會發生任何程序之外。</span><span class="sxs-lookup"><span data-stu-id="5205f-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="5205f-104">允許只宣告外部程序。</span><span class="sxs-lookup"><span data-stu-id="5205f-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="5205f-105">或者，程式設計項目宣告時沒有宣告關鍵字這類`Dim`或`Const`。</span><span class="sxs-lookup"><span data-stu-id="5205f-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="5205f-106">**錯誤 ID:** BC30188</span><span class="sxs-lookup"><span data-stu-id="5205f-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5205f-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5205f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="5205f-108">非宣告的陳述式移至程序的主體。</span><span class="sxs-lookup"><span data-stu-id="5205f-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
-   <span data-ttu-id="5205f-109">開始使用適當的宣告關鍵字宣告。</span><span class="sxs-lookup"><span data-stu-id="5205f-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
-   <span data-ttu-id="5205f-110">請確定宣告關鍵字沒有拼字錯誤。</span><span class="sxs-lookup"><span data-stu-id="5205f-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5205f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5205f-111">See also</span></span>

- [<span data-ttu-id="5205f-112">程序</span><span class="sxs-lookup"><span data-stu-id="5205f-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="5205f-113">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5205f-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
