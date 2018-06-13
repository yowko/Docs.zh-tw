---
title: 判斷服務作業持續時間
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 8c86ccc09979071e0678be792f4937d526e23fa7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804959"
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="b9977-102">判斷服務作業持續時間</span><span class="sxs-lookup"><span data-stu-id="b9977-102">Determining service operation duration</span></span>
<span data-ttu-id="b9977-103">如果分析追蹤已啟用 Windows Communication Foundation (WCF) 應用程式中，服務作業執行期間可以輕鬆地檢查事件記錄檔來判斷。</span><span class="sxs-lookup"><span data-stu-id="b9977-103">If analytic tracing is enabled in a Windows Communication Foundation (WCF) application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="b9977-104">本主題示範如何判斷服務作業完成所需的時間。</span><span class="sxs-lookup"><span data-stu-id="b9977-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="b9977-105">判斷服務作業執行持續時間</span><span class="sxs-lookup"><span data-stu-id="b9977-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="b9977-106">開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。</span><span class="sxs-lookup"><span data-stu-id="b9977-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="b9977-107">如果您尚未啟用分析追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**.</span><span class="sxs-lookup"><span data-stu-id="b9977-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b9977-108">選取**檢視**，**顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="b9977-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="b9977-109">以滑鼠右鍵按一下**分析**選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="b9977-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="b9977-110">讓 [事件檢視器] 保持開啟狀態，如此在服務作業執行之後就能檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="b9977-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="b9977-111">接下來，開啟包含服務專案，以及與該服務互動的用戶端專案的 WCF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9977-111">Next, open a WCF application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="b9977-112">您可以建立這類應用程式遵循[入門教學課程](../../../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="b9977-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="b9977-113">如果您有安裝 WCF 範例，您可以開啟[入門](../../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含已完成本教學課程中建立的專案。</span><span class="sxs-lookup"><span data-stu-id="b9977-113">If you have the WCF samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="b9977-114">執行伺服器應用程式按**F5**。</span><span class="sxs-lookup"><span data-stu-id="b9977-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="b9977-115">執行用戶端應用程式，以滑鼠右鍵按一下**用戶端**專案，並選取**偵錯**，**開始新執行個體**。</span><span class="sxs-lookup"><span data-stu-id="b9977-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="b9977-116">在 [事件檢視器] 中，重新整理分析記錄檔並依照 [事件 ID] 排序事件。</span><span class="sxs-lookup"><span data-stu-id="b9977-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="b9977-117">尋找事件識別碼[214-operationcompleted，接續](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)。</span><span class="sxs-lookup"><span data-stu-id="b9977-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="b9977-118">這些事件將顯示已完成的作業，以及作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="b9977-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="b9977-119">下列事件會顯示 Add 作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="b9977-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
