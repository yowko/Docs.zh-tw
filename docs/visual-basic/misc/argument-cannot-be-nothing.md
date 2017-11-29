---
title: "引數不能為 Nothing"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a54cf0ed9e2b307174c1be0e853a920dfc94202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="1a494-102">引數不能為 Nothing</span><span class="sxs-lookup"><span data-stu-id="1a494-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="1a494-103">Null 值已提供給必須有值的引數。</span><span class="sxs-lookup"><span data-stu-id="1a494-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a494-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1a494-104">To correct this error</span></span>  
  
-   <span data-ttu-id="1a494-105">您可能嘗試使用物件，卻未提供該物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1a494-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="1a494-106">這種情況請使用 `New` 關鍵字建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="1a494-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="1a494-107">檢查值是否計算正確。</span><span class="sxs-lookup"><span data-stu-id="1a494-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a494-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a494-108">See Also</span></span>  
 [<span data-ttu-id="1a494-109">疑難排解例外狀況：System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="1a494-109">Troubleshooting Exceptions: System.NullReferenceException</span></span>](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
