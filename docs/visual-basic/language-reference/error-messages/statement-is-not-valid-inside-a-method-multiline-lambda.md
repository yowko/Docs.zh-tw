---
title: 陳述式在具有多行的方法 lambda 內無效
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: d5d756f1772b9519613e163119b88a3057d36cf3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870617"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="e5eab-102">陳述式在方法/多行 Lambda 內無效</span><span class="sxs-lookup"><span data-stu-id="e5eab-102">Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="e5eab-103">`Sub`、 `Function` 、屬性 `Get` 或屬性程式中的語句無效 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="e5eab-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="e5eab-104">某些語句可放置在模組或類別層級。</span><span class="sxs-lookup"><span data-stu-id="e5eab-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="e5eab-105">其他（例如 `Option Strict` ）必須位於命名空間層級，且必須在所有其他宣告之前。</span><span class="sxs-lookup"><span data-stu-id="e5eab-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="e5eab-106">**錯誤識別碼：** BC30024</span><span class="sxs-lookup"><span data-stu-id="e5eab-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5eab-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e5eab-107">To correct this error</span></span>  
  
- <span data-ttu-id="e5eab-108">從程式中移除語句。</span><span class="sxs-lookup"><span data-stu-id="e5eab-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5eab-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5eab-109">See also</span></span>

- [<span data-ttu-id="e5eab-110">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="e5eab-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="e5eab-111">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="e5eab-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="e5eab-112">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="e5eab-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="e5eab-113">Set 語句</span><span class="sxs-lookup"><span data-stu-id="e5eab-113">Set Statement</span></span>](../statements/set-statement.md)
