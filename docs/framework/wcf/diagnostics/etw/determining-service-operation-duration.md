---
title: 判斷服務作業持續時間
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 9bc38f40b22eca8278905440ee69af9f38b81a0d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798107"
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="4ba63-102">判斷服務作業持續時間</span><span class="sxs-lookup"><span data-stu-id="4ba63-102">Determining service operation duration</span></span>
<span data-ttu-id="4ba63-103">如果已在 Windows Communication Foundation （WCF）應用程式中啟用分析追蹤，則可以藉由檢查事件記錄檔，輕鬆地判斷服務作業的執行持續時間。</span><span class="sxs-lookup"><span data-stu-id="4ba63-103">If analytic tracing is enabled in a Windows Communication Foundation (WCF) application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="4ba63-104">本主題示範如何判斷服務作業完成所需的時間。</span><span class="sxs-lookup"><span data-stu-id="4ba63-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="4ba63-105">判斷服務作業執行持續時間</span><span class="sxs-lookup"><span data-stu-id="4ba63-105">Determining service operation execution duration</span></span>  
  
1. <span data-ttu-id="4ba63-106">按一下 [**開始**]、[**執行**]，然後`eventvwr.exe`輸入，以開啟事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="4ba63-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2. <span data-ttu-id="4ba63-107">如果您尚未啟用分析追蹤，請展開 [**應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**]、[**應用程式伺服器**]。</span><span class="sxs-lookup"><span data-stu-id="4ba63-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="4ba63-108">選取 [ **View**]、[**顯示分析和調試記錄**]。</span><span class="sxs-lookup"><span data-stu-id="4ba63-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="4ba63-109">以滑鼠右鍵按一下 [**分析**]，然後選取 [**啟用記錄**]。</span><span class="sxs-lookup"><span data-stu-id="4ba63-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="4ba63-110">讓 [事件檢視器] 保持開啟狀態，如此在服務作業執行之後就能檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="4ba63-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3. <span data-ttu-id="4ba63-111">接下來，開啟包含服務專案的 WCF 應用程式，以及與該服務互動的用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="4ba63-111">Next, open a WCF application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="4ba63-112">您可以遵循[消費者入門教學](../../getting-started-tutorial.md)課程來建立這類應用程式。</span><span class="sxs-lookup"><span data-stu-id="4ba63-112">You can create such an application by following the [Getting Started Tutorial](../../getting-started-tutorial.md).</span></span>  <span data-ttu-id="4ba63-113">如果您已安裝 WCF 範例，可以開啟[消費者入門](../../samples/getting-started-sample.md)，其中包含在教學課程中建立的已完成專案。</span><span class="sxs-lookup"><span data-stu-id="4ba63-113">If you have the WCF samples installed, you can open the [Getting Started](../../samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4. <span data-ttu-id="4ba63-114">按**F5**執行伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="4ba63-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="4ba63-115">以滑鼠右鍵按一下**用戶端**專案，然後選取 [ **Debug**]、[**開始新實例**]，來執行用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="4ba63-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5. <span data-ttu-id="4ba63-116">在 [事件檢視器] 中，重新整理分析記錄檔並依照 [事件 ID] 排序事件。</span><span class="sxs-lookup"><span data-stu-id="4ba63-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="4ba63-117">尋找事件識別碼為[214-OperationCompleted](214-operationcompleted.md)的事件。</span><span class="sxs-lookup"><span data-stu-id="4ba63-117">Look for events with Event ID [214 - OperationCompleted](214-operationcompleted.md).</span></span>  <span data-ttu-id="4ba63-118">這些事件將顯示已完成的作業，以及作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="4ba63-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="4ba63-119">下列事件會顯示 Add 作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="4ba63-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
