---
title: 陳述式在具有多行的方法 lambda 內無效
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef992c3eaa2b82bbf5e8993f9fccd64ae388c95
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159673"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="22962-102">BC30024：在方法/多行 lambda 內的語句無效</span><span class="sxs-lookup"><span data-stu-id="22962-102">BC30024: Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="22962-103">`Sub`、 `Function` 、屬性 `Get` 或屬性程式中的語句無效 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="22962-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="22962-104">某些語句可放置在模組或類別層級。</span><span class="sxs-lookup"><span data-stu-id="22962-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="22962-105">其他（例如 `Option Strict` ）必須位於命名空間層級，且必須在所有其他宣告之前。</span><span class="sxs-lookup"><span data-stu-id="22962-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>

 <span data-ttu-id="22962-106">**錯誤識別碼：** BC30024</span><span class="sxs-lookup"><span data-stu-id="22962-106">**Error ID:** BC30024</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="22962-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="22962-107">To correct this error</span></span>

- <span data-ttu-id="22962-108">從程式中移除語句。</span><span class="sxs-lookup"><span data-stu-id="22962-108">Remove the statement from the procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="22962-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22962-109">See also</span></span>

- [<span data-ttu-id="22962-110">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="22962-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="22962-111">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="22962-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="22962-112">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="22962-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="22962-113">Set 語句</span><span class="sxs-lookup"><span data-stu-id="22962-113">Set Statement</span></span>](../statements/set-statement.md)
