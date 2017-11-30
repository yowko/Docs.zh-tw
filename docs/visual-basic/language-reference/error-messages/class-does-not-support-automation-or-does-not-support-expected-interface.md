---
title: "類別不支援 Automation 或不支援預期的介面"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6528ceabeb7fb7a1cdc0beff2fd362632a0a0c9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="54d91-102">類別不支援 Automation 或不支援預期的介面</span><span class="sxs-lookup"><span data-stu-id="54d91-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="54d91-103">您在 `GetObject` 或 `CreateObject` 函式呼叫中指定的類別沒有公開撰寫程式介面，或是您將專案從 .dll 變更為 .exe (反之亦然)。</span><span class="sxs-lookup"><span data-stu-id="54d91-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="54d91-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="54d91-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="54d91-105">查看建立物件的應用程式文件，以取得此物件類別的自動化使用限制。</span><span class="sxs-lookup"><span data-stu-id="54d91-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2.  <span data-ttu-id="54d91-106">如果您將專案從 .dll 變更為 .exe (反之亦然)，則必須手動移除舊 .dll 或 .exe 的註冊。</span><span class="sxs-lookup"><span data-stu-id="54d91-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d91-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54d91-107">See Also</span></span>  
 [<span data-ttu-id="54d91-108">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="54d91-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="54d91-109">告訴我們</span><span class="sxs-lookup"><span data-stu-id="54d91-109">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
