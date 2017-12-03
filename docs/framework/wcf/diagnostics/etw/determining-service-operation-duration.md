---
title: "判斷服務作業持續時間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24f1bc22e088c0198ec8a8f8183611d2b43941b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="7b2a7-102">判斷服務作業持續時間</span><span class="sxs-lookup"><span data-stu-id="7b2a7-102">Determining service operation duration</span></span>
<span data-ttu-id="7b2a7-103">如果已啟用 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中的分析追蹤，則透過檢查事件記錄檔就能輕鬆判斷出服務作業的執行持續時間。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-103">If analytic tracing is enabled in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="7b2a7-104">本主題示範如何判斷服務作業完成所需的時間。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="7b2a7-105">判斷服務作業執行持續時間</span><span class="sxs-lookup"><span data-stu-id="7b2a7-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="7b2a7-106">開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="7b2a7-107">如果您尚未啟用分析追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**.</span><span class="sxs-lookup"><span data-stu-id="7b2a7-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="7b2a7-108">選取**檢視**，**顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="7b2a7-109">以滑鼠右鍵按一下**分析**選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="7b2a7-110">讓 [事件檢視器] 保持開啟狀態，如此在服務作業執行之後就能檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="7b2a7-111">接著開啟 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 應用程式，其中包括與該服務互動的服務專案和用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-111">Next, open a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="7b2a7-112">您可以建立這類應用程式遵循[入門教學課程](../../../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="7b2a7-113">如果您有[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]範例的安裝，您可以開啟[入門](../../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含已完成本教學課程中建立的專案。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-113">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="7b2a7-114">執行伺服器應用程式按**F5**。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="7b2a7-115">執行用戶端應用程式，以滑鼠右鍵按一下**用戶端**專案，並選取**偵錯**，**開始新執行個體**。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="7b2a7-116">在 [事件檢視器] 中，重新整理分析記錄檔並依照 [事件 ID] 排序事件。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="7b2a7-117">尋找事件識別碼[214-operationcompleted，接續](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="7b2a7-118">這些事件將顯示已完成的作業，以及作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="7b2a7-119">下列事件會顯示 Add 作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="7b2a7-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
