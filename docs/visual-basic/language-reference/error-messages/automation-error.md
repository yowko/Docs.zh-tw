---
title: "Automation 錯誤 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID440
dev_langs:
- VB
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b48ada07663889db633a43fabb577d5129c5cbb3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="automation-error"></a><span data-ttu-id="ca125-102">Automation 錯誤</span><span class="sxs-lookup"><span data-stu-id="ca125-102">Automation error</span></span>
<span data-ttu-id="ca125-103">執行方法，或取得或設定物件變數的屬性時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca125-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="ca125-104">錯誤由建立物件的應用程式所回報。</span><span class="sxs-lookup"><span data-stu-id="ca125-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca125-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ca125-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="ca125-106">檢查 `Err` 物件的屬性，判斷錯誤的來源和本質。</span><span class="sxs-lookup"><span data-stu-id="ca125-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="ca125-107">在存取陳述式之前使用 `On Error Resume Next` 陳述式，然後在存取陳述式之後立即檢查錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca125-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca125-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca125-108">See Also</span></span>  
 <span data-ttu-id="ca125-109">[錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="ca125-109">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="ca125-110"> [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="ca125-110"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
