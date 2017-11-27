---
title: "發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="946b7-102">發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="946b7-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="946b7-103">應用程式無法取得必要的作業系統資源。</span><span class="sxs-lookup"><span data-stu-id="946b7-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="946b7-104">此問題的部分可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="946b7-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="946b7-105">應用程式沒有權限可建立具名的作業系統物件。</span><span class="sxs-lookup"><span data-stu-id="946b7-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="946b7-106">通用語言執行平台沒有權限可建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="946b7-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="946b7-107">應用程式需要存取作業系統物件，但另一個處理序正在使用它。</span><span class="sxs-lookup"><span data-stu-id="946b7-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="946b7-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="946b7-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="946b7-109">檢查應用程式有足夠的權限可建立指名的作業系統物件。</span><span class="sxs-lookup"><span data-stu-id="946b7-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="946b7-110">檢查通用語言執行平台有足夠的權限可建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="946b7-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="946b7-111">重新啟動電腦，以清除可能正在使用連接到原始執行個體應用程式之所需資源的任何處理序。</span><span class="sxs-lookup"><span data-stu-id="946b7-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="946b7-112">記下錯誤發生時的情況，並致電 Microsoft 產品支援服務</span><span class="sxs-lookup"><span data-stu-id="946b7-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946b7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="946b7-113">See Also</span></span>  
 [<span data-ttu-id="946b7-114">專案設計工具、應用程式頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946b7-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="946b7-115">偵錯工具基礎</span><span class="sxs-lookup"><span data-stu-id="946b7-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="946b7-116">告訴我們</span><span class="sxs-lookup"><span data-stu-id="946b7-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
