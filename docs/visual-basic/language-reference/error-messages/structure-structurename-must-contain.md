---
title: "結構 &#39;&lt;structurename&gt;&#39; 必須包含至少一個執行個體成員變數或至少一個執行個體事件宣告未標記為 &#39;自訂 &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords: BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="06de5-102">結構 &#39;&lt;structurename&gt;&#39; 必須包含至少一個執行個體成員變數或至少一個執行個體事件宣告未標記為 &#39;自訂 &#39;</span><span class="sxs-lookup"><span data-stu-id="06de5-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="06de5-103">結構定義不包含任何非共用的變數或非共用的非自訂事件。</span><span class="sxs-lookup"><span data-stu-id="06de5-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="06de5-104">每個結構必須具有的變數或套用至每個特定執行個體 （共用） 而不是所有執行個體共同的事件 ([共用](../../../visual-basic/language-reference/modifiers/shared.md))。</span><span class="sxs-lookup"><span data-stu-id="06de5-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="06de5-105">非共用的常數、 屬性和程序不符合此需求。</span><span class="sxs-lookup"><span data-stu-id="06de5-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="06de5-106">此外，如果有非共用的變數，且只能有一個非共用的事件，該事件不可以是`Custom`事件。</span><span class="sxs-lookup"><span data-stu-id="06de5-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="06de5-107">**錯誤 ID:** BC30941</span><span class="sxs-lookup"><span data-stu-id="06de5-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="06de5-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="06de5-108">To correct this error</span></span>  
  
-   <span data-ttu-id="06de5-109">定義至少一個變數或不是事件`Shared`。</span><span class="sxs-lookup"><span data-stu-id="06de5-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="06de5-110">如果您定義只有一個事件，它必須是非自訂，以及非共用。</span><span class="sxs-lookup"><span data-stu-id="06de5-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06de5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06de5-111">See Also</span></span>  
 [<span data-ttu-id="06de5-112">結構</span><span class="sxs-lookup"><span data-stu-id="06de5-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="06de5-113">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="06de5-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="06de5-114">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="06de5-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
