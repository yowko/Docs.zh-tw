---
title: "總和檢查碼錯誤值，非十六進位數字或奇數的十六進位數字 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42033
- vbc42033
dev_langs:
- VB
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
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
ms.openlocfilehash: 70a8fc5e0200c15858ad1288e12b2aeb1e5303d8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="1b29b-102">錯誤的總和檢查碼值，非十六進位數字或奇數的十六進位數字</span><span class="sxs-lookup"><span data-stu-id="1b29b-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="1b29b-103">總和檢查碼值包含無效的十六進位數字，或是有奇數個數字。</span><span class="sxs-lookup"><span data-stu-id="1b29b-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="1b29b-104">當 ASP.NET 產生 Visual Basic 原始程式檔 (副檔名為 .vb) 時，它會計算總和檢查碼並將它放在 `#externalchecksum` 所識別的隱藏原始程式檔中。</span><span class="sxs-lookup"><span data-stu-id="1b29b-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="1b29b-105">使用者產生 .vb 檔案也可能這麼做，但這個流程最好留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="1b29b-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="1b29b-106">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="1b29b-106">By default, this message is a warning.</span></span> <span data-ttu-id="1b29b-107">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="1b29b-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1b29b-108">**錯誤識別碼︰** BC42033</span><span class="sxs-lookup"><span data-stu-id="1b29b-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1b29b-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1b29b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="1b29b-110">如果 ASP.NET 正在產生 Visual Basic 原始程式檔，請重新啟動專案建置。</span><span class="sxs-lookup"><span data-stu-id="1b29b-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2.  <span data-ttu-id="1b29b-111">如果這個警告在重新啟動之後持續發生，請重新安裝 ASP.NET 然後重試建置。</span><span class="sxs-lookup"><span data-stu-id="1b29b-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3.  <span data-ttu-id="1b29b-112">如果警告仍然持續發生，或您未使用 ASP.NET，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="1b29b-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b29b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b29b-113">See Also</span></span>  
 <span data-ttu-id="1b29b-114">[ASP.NET 概觀](https://msdn.microsoft.com/library/4w3ex9c2.aspx) </span><span class="sxs-lookup"><span data-stu-id="1b29b-114">[ASP.NET Overview](https://msdn.microsoft.com/library/4w3ex9c2.aspx) </span></span>  
<span data-ttu-id="1b29b-115"> [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="1b29b-115"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
