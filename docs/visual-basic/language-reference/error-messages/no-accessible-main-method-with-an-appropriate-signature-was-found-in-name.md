---
title: 在 '<name>' 中找不到具有適當簽名碼的可存取 'Main' 方法
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6760b931ceb2ad5c2c04169d664da8629badc487
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409409"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="5b0e3-102">在 '\<name>' 中找不到具有適當簽名碼的可存取 'Main' 方法</span><span class="sxs-lookup"><span data-stu-id="5b0e3-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="5b0e3-103">命令列應用程式必須已 `Sub Main` 定義。</span><span class="sxs-lookup"><span data-stu-id="5b0e3-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="5b0e3-104">`Main`必須宣告為 `Public Shared` 在類別中定義，或如同 `Public` 在模組中定義一樣。</span><span class="sxs-lookup"><span data-stu-id="5b0e3-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="5b0e3-105">**錯誤識別碼：** BC30737</span><span class="sxs-lookup"><span data-stu-id="5b0e3-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5b0e3-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5b0e3-106">To correct this error</span></span>  
  
- <span data-ttu-id="5b0e3-107">定義專案的程式 `Public Sub Main` 。</span><span class="sxs-lookup"><span data-stu-id="5b0e3-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="5b0e3-108">`Shared`只有當您在類別內定義它時，才將它宣告為。</span><span class="sxs-lookup"><span data-stu-id="5b0e3-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0e3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b0e3-109">See also</span></span>

- [<span data-ttu-id="5b0e3-110">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="5b0e3-110">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="5b0e3-111">程序</span><span class="sxs-lookup"><span data-stu-id="5b0e3-111">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
