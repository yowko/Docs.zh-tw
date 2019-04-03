---
title: Automation 錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: e0ebaabb14cf5685469f88b0be3b7fece017165e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843652"
---
# <a name="automation-error"></a><span data-ttu-id="9b4a9-102">Automation 錯誤</span><span class="sxs-lookup"><span data-stu-id="9b4a9-102">Automation error</span></span>
<span data-ttu-id="9b4a9-103">執行方法，或取得或設定物件變數的屬性時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b4a9-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="9b4a9-104">錯誤由建立物件的應用程式所回報。</span><span class="sxs-lookup"><span data-stu-id="9b4a9-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9b4a9-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9b4a9-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="9b4a9-106">檢查 `Err` 物件的屬性，判斷錯誤的來源和本質。</span><span class="sxs-lookup"><span data-stu-id="9b4a9-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="9b4a9-107">在存取陳述式之前使用 `On Error Resume Next` 陳述式，然後在存取陳述式之後立即檢查錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b4a9-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4a9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b4a9-108">See also</span></span>

- [<span data-ttu-id="9b4a9-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="9b4a9-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9b4a9-110">告訴我們</span><span class="sxs-lookup"><span data-stu-id="9b4a9-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
