---
title: "此單一執行個體應用程式無法連線到原始執行個體 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 113923e7cb72d1da0a8fb289f29e9afa60dda558
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="a5ab7-102">此單一執行個體應用程式無法連接到原始執行個體</span><span class="sxs-lookup"><span data-stu-id="a5ab7-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="a5ab7-103">此單一執行個體應用程式無法連接到原始執行個體。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="a5ab7-104">此問題的部分可能原因如下：</span><span class="sxs-lookup"><span data-stu-id="a5ab7-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="a5ab7-105">原始執行個體停止回應。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="a5ab7-106">應用程式沒有建立核心物件的權限。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="a5ab7-107">如需核心物件的詳細資訊，請參閱[Mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-107">For more information about kernel objects, see [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).</span></span>  
  
     <span data-ttu-id="a5ab7-108">核心物件的主檔名 (Base Name) 是由連接組件的 GUID、主要版本號碼，以及次要版本號碼所組成。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="a5ab7-109">例如，基底名稱可能是 `3639f15d-9547-43da-8145-60da347829915.1`。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="a5ab7-110">在開發應用程式時更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a5ab7-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="a5ab7-111">檢查應用程式並未進入沒有回應的狀態。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="a5ab7-112">檢查應用程式有足夠的權限可建立核心物件。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="a5ab7-113">重新啟動應用程式的原始執行個體。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="a5ab7-114">重新啟動電腦，以針對連接到原始執行個體應用程式所需的資源，清除可能正在使用它的任何處理序。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="a5ab7-115">記下錯誤發生時的情況，並致電 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ab7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5ab7-116">See Also</span></span>  
 <span data-ttu-id="a5ab7-117">[NIB: How to︰ 指定應用程式 (Visual Basic) 的執行個體行為](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e) </span><span class="sxs-lookup"><span data-stu-id="a5ab7-117">[NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e) </span></span>  
<span data-ttu-id="a5ab7-118"> [偵錯工具基本概念](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span><span class="sxs-lookup"><span data-stu-id="a5ab7-118"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span></span>  
<span data-ttu-id="a5ab7-119"> [PAVEOVER 產品支援和可及性](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)</span><span class="sxs-lookup"><span data-stu-id="a5ab7-119"> [PAVEOVER Product Support and Accessibility](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)</span></span>
