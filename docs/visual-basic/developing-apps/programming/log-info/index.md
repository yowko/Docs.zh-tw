---
title: 記錄來自應用程式的資訊 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 68ec09dac026e46716ff18dce88acf9d60635026
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881927"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="87379-102">記錄來自應用程式的資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87379-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="87379-103">本節包含的主題說明如何使用 `My.Application.Log` 或 `My.Log` 物件記錄來自應用程式的資訊，以及如何擴充應用程式的記錄功能。</span><span class="sxs-lookup"><span data-stu-id="87379-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="87379-104">`Log` 物件可提供將資訊寫入應用程式記錄檔接聽程式的方法，而 `Log` 物件的進階 `TraceSource` 屬性則提供詳細組態資訊。</span><span class="sxs-lookup"><span data-stu-id="87379-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="87379-105">`Log` 物件是由應用程式的組態檔進行設定。</span><span class="sxs-lookup"><span data-stu-id="87379-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="87379-106">`My.Log` 物件僅適用於 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="87379-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="87379-107">若是用戶端應用程式，請使用 `My.Application.Log`。</span><span class="sxs-lookup"><span data-stu-id="87379-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="87379-108">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Logging.Log>。</span><span class="sxs-lookup"><span data-stu-id="87379-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="87379-109">工作</span><span class="sxs-lookup"><span data-stu-id="87379-109">Tasks</span></span>  
  
|<span data-ttu-id="87379-110">以</span><span class="sxs-lookup"><span data-stu-id="87379-110">To</span></span>|<span data-ttu-id="87379-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="87379-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="87379-112">將事件資訊寫入應用程式的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87379-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="87379-113">如何：寫入記錄檔訊息</span><span class="sxs-lookup"><span data-stu-id="87379-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="87379-114">將例外狀況資訊寫入應用程式的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87379-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="87379-115">如何：記錄例外狀況</span><span class="sxs-lookup"><span data-stu-id="87379-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="87379-116">在應用程式啟動和關閉時，將追蹤資訊寫入應用程式的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87379-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="87379-117">如何：在應用程式啟動或關閉時記錄訊息</span><span class="sxs-lookup"><span data-stu-id="87379-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="87379-118">設定 `My.Application.Log` 以將資訊寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="87379-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="87379-119">如何：將事件資訊寫入至文字檔</span><span class="sxs-lookup"><span data-stu-id="87379-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="87379-120">設定 `My.Application.Log` 以將資訊寫入事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87379-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="87379-121">如何：寫入應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="87379-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="87379-122">變更 `My.Application.Log` 寫入資訊的位置。</span><span class="sxs-lookup"><span data-stu-id="87379-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="87379-123">逐步解說：變更 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="87379-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="87379-124">判斷 `My.Application.Log` 寫入資訊的位置。</span><span class="sxs-lookup"><span data-stu-id="87379-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="87379-125">逐步解說：判斷 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="87379-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="87379-126">建立 `My.Application.Log` 的自訂記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="87379-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="87379-127">逐步解說：建立自訂的記錄檔接聽程式</span><span class="sxs-lookup"><span data-stu-id="87379-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="87379-128">篩選 `My.Application.Log` 記錄檔的輸出。</span><span class="sxs-lookup"><span data-stu-id="87379-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="87379-129">逐步解說：篩選 My.Application.Log 輸出</span><span class="sxs-lookup"><span data-stu-id="87379-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="87379-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="87379-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="87379-131">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="87379-131">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="87379-132">疑難排解：記錄檔接聽程式</span><span class="sxs-lookup"><span data-stu-id="87379-132">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
