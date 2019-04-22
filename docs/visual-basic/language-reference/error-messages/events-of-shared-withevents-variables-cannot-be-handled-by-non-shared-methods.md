---
title: 共用 WithEvents 變數的事件不能由非共用的方法處理
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838647"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="30326-102">共用 WithEvents 變數的事件不能由非共用的方法處理</span><span class="sxs-lookup"><span data-stu-id="30326-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="30326-103">以宣告的變數`Shared`修飾詞是共用的變數。</span><span class="sxs-lookup"><span data-stu-id="30326-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="30326-104">共用的變數會識別一個儲存體位置。</span><span class="sxs-lookup"><span data-stu-id="30326-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="30326-105">以宣告的變數`WithEvents`修飾詞會判斷提示變數所屬的類型處理的變數會引發的事件集。</span><span class="sxs-lookup"><span data-stu-id="30326-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="30326-106">屬性時的值指派給變數時，已由`WithEvents`宣告會解除鎖定的任何現有的事件處理常式，並透過新的事件處理常式連結`Add`方法。</span><span class="sxs-lookup"><span data-stu-id="30326-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="30326-107">**錯誤 ID:** BC30594</span><span class="sxs-lookup"><span data-stu-id="30326-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="30326-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="30326-108">To correct this error</span></span>  
  
-   <span data-ttu-id="30326-109">宣告事件處理常式`Shared`。</span><span class="sxs-lookup"><span data-stu-id="30326-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30326-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30326-110">See also</span></span>

- [<span data-ttu-id="30326-111">Shared</span><span class="sxs-lookup"><span data-stu-id="30326-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="30326-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="30326-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
