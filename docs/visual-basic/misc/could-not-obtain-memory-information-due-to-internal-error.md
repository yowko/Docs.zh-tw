---
title: "由於內部錯誤，無法取得記憶體資訊"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bf339e34368df8fb03024cec255e39e6992be77f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a><span data-ttu-id="45949-102">由於內部錯誤，無法取得記憶體資訊</span><span class="sxs-lookup"><span data-stu-id="45949-102">Could not obtain memory information due to internal error</span></span>
<span data-ttu-id="45949-103">呼叫 `My.Computer.Info` 物件的其中一個記憶體資訊屬性失敗。</span><span class="sxs-lookup"><span data-stu-id="45949-103">A call to one of the memory-information properties of the `My.Computer.Info` object failed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45949-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="45949-104">To correct this error</span></span>  
  
-   <span data-ttu-id="45949-105">在 `Try...Catch` 物件之記憶體資訊屬性的呼叫周圍加入 `My.Computer.Info` 區塊。</span><span class="sxs-lookup"><span data-stu-id="45949-105">Add a `Try...Catch` block around the call to the memory-information property of the `My.Computer.Info` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45949-106">請參閱</span><span class="sxs-lookup"><span data-stu-id="45949-106">See Also</span></span>  
 [<span data-ttu-id="45949-107">My.Computer.Info</span><span class="sxs-lookup"><span data-stu-id="45949-107">My.Computer.Info</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo)  
 [<span data-ttu-id="45949-108">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="45949-108">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
