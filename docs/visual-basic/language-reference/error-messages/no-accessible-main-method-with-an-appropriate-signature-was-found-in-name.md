---
title: 在 '<name>' 中找不到具有適當簽名碼的可存取 'Main' 方法
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: f5053bddf4b9ba791ad6d0733e1dd89c4ded91bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918264"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="12832-102">在找不到具有適當簽章沒有存取 'Main' 方法 '\<名稱 >'</span><span class="sxs-lookup"><span data-stu-id="12832-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="12832-103">命令列應用程式必須具備`Sub Main`定義。</span><span class="sxs-lookup"><span data-stu-id="12832-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="12832-104">`Main` 必須宣告為`Public Shared`如果已定義在類別中，或為`Public`如果模組中定義。</span><span class="sxs-lookup"><span data-stu-id="12832-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="12832-105">**錯誤 ID:** BC30737</span><span class="sxs-lookup"><span data-stu-id="12832-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12832-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="12832-106">To correct this error</span></span>  
  
-   <span data-ttu-id="12832-107">定義`Public Sub Main`程序，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="12832-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="12832-108">將它宣告為`Shared`如果且只有在類別內定義它。</span><span class="sxs-lookup"><span data-stu-id="12832-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12832-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12832-109">See also</span></span>

- [<span data-ttu-id="12832-110">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="12832-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="12832-111">程序</span><span class="sxs-lookup"><span data-stu-id="12832-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
