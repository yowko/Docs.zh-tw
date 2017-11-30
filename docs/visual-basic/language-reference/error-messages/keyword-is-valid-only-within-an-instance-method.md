---
title: "&#39;&lt;關鍵字&gt;&#39; 只能在執行個體方法"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords: BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="b100a-102">&#39;&lt;關鍵字&gt;&#39; 只能在執行個體方法</span><span class="sxs-lookup"><span data-stu-id="b100a-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="b100a-103">`Me`， `MyClass`，和`MyBase`關鍵字參考特定的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="b100a-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="b100a-104">您無法使用它們內共用`Function`或`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="b100a-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="b100a-105">**錯誤 ID:** BC30043</span><span class="sxs-lookup"><span data-stu-id="b100a-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b100a-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b100a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b100a-107">移除程序中的關鍵字，或移除`Shared`程序宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b100a-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b100a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b100a-108">See Also</span></span>  
 [<span data-ttu-id="b100a-109">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="b100a-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="b100a-110">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="b100a-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="b100a-111">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="b100a-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
