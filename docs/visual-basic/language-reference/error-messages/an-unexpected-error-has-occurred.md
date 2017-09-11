---
title: "已發生意外的錯誤，因為無法取得單一執行個體啟動時所需要的作業系統資源 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
dev_langs:
- VB
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
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
ms.openlocfilehash: 03ab2d1c746fbc28c0c6f3e59371cc6bbd4050cd
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="331a9-102">發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="331a9-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="331a9-103">應用程式無法取得必要的作業系統資源。</span><span class="sxs-lookup"><span data-stu-id="331a9-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="331a9-104">此問題的部分可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="331a9-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="331a9-105">應用程式沒有權限可建立具名的作業系統物件。</span><span class="sxs-lookup"><span data-stu-id="331a9-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="331a9-106">通用語言執行平台沒有權限可建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="331a9-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="331a9-107">應用程式需要存取作業系統物件，但另一個處理序正在使用它。</span><span class="sxs-lookup"><span data-stu-id="331a9-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="331a9-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="331a9-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="331a9-109">檢查應用程式有足夠的權限可建立指名的作業系統物件。</span><span class="sxs-lookup"><span data-stu-id="331a9-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="331a9-110">檢查通用語言執行平台有足夠的權限可建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="331a9-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="331a9-111">重新啟動電腦，以清除可能正在使用連接到原始執行個體應用程式之所需資源的任何處理序。</span><span class="sxs-lookup"><span data-stu-id="331a9-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="331a9-112">記下錯誤發生時的情況，並致電 Microsoft 產品支援服務</span><span class="sxs-lookup"><span data-stu-id="331a9-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331a9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="331a9-113">See Also</span></span>  
 <span data-ttu-id="331a9-114">[專案設計工具、應用程式頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="331a9-114">[Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="331a9-115"> [偵錯工具基本概念](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span><span class="sxs-lookup"><span data-stu-id="331a9-115"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span></span>  
<span data-ttu-id="331a9-116"> [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="331a9-116"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
