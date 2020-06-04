---
title: 陳述式在具有多行的方法 lambda 內無效
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: f3c43d640259d5e1af545e2610088aab5d70453d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396242"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="db789-102">陳述式在方法/多行 Lambda 內無效</span><span class="sxs-lookup"><span data-stu-id="db789-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="db789-103">語句在 `Sub` 、 `Function` 、屬性 `Get` 或屬性程式中無效 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="db789-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="db789-104">有些語句可以放在模組或類別層級。</span><span class="sxs-lookup"><span data-stu-id="db789-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="db789-105">其他專案（例如 `Option Strict` ）必須位於命名空間層級，且在其他所有宣告之前。</span><span class="sxs-lookup"><span data-stu-id="db789-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="db789-106">**錯誤識別碼：** BC30024</span><span class="sxs-lookup"><span data-stu-id="db789-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db789-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="db789-107">To correct this error</span></span>  
  
- <span data-ttu-id="db789-108">請移除程式中的語句。</span><span class="sxs-lookup"><span data-stu-id="db789-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db789-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db789-109">See also</span></span>

- [<span data-ttu-id="db789-110">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="db789-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="db789-111">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="db789-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="db789-112">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="db789-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="db789-113">Set 語句</span><span class="sxs-lookup"><span data-stu-id="db789-113">Set Statement</span></span>](../statements/set-statement.md)
