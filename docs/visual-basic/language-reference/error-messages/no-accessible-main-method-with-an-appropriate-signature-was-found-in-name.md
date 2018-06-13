---
title: 沒有可存取&#39;Main&#39;中找不到具有適當簽章的方法&#39;&lt;名稱&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593216"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="6c2c0-102">沒有可存取&#39;Main&#39;中找不到具有適當簽章的方法&#39;&lt;名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="6c2c0-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="6c2c0-103">命令列應用程式必須具備`Sub Main`定義。</span><span class="sxs-lookup"><span data-stu-id="6c2c0-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="6c2c0-104">`Main` 必須宣告為`Public Shared`如果已定義在類別中，或做為`Public`如果的模組中定義。</span><span class="sxs-lookup"><span data-stu-id="6c2c0-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="6c2c0-105">**錯誤 ID:** BC30737</span><span class="sxs-lookup"><span data-stu-id="6c2c0-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6c2c0-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6c2c0-106">To correct this error</span></span>  
  
-   <span data-ttu-id="6c2c0-107">定義`Public Sub Main`程序，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="6c2c0-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="6c2c0-108">將它宣告為`Shared`如果且只有在類別內定義它。</span><span class="sxs-lookup"><span data-stu-id="6c2c0-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2c0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c2c0-109">See Also</span></span>  
 [<span data-ttu-id="6c2c0-110">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="6c2c0-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="6c2c0-111">程序</span><span class="sxs-lookup"><span data-stu-id="6c2c0-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
