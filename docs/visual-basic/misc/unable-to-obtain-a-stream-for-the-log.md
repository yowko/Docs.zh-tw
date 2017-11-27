---
title: "無法取得記錄檔的資料流"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="c835f-102">無法取得記錄檔的資料流</span><span class="sxs-lookup"><span data-stu-id="c835f-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="c835f-103">無法取得記錄檔的資料流。</span><span class="sxs-lookup"><span data-stu-id="c835f-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="c835f-104">根據的檔名\<名稱 > 已在使用中。</span><span class="sxs-lookup"><span data-stu-id="c835f-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="c835f-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>類別無法建立新的記錄檔，因為所有潛在的記錄檔名稱為基礎\<名稱 > 已在使用中。</span><span class="sxs-lookup"><span data-stu-id="c835f-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="c835f-106">記錄檔太多可能表示應用程式發生架構問題。</span><span class="sxs-lookup"><span data-stu-id="c835f-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="c835f-107">如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="c835f-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c835f-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c835f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c835f-109">請將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> 或 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> ，以在記錄檔名稱中包括日期戳記。</span><span class="sxs-lookup"><span data-stu-id="c835f-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="c835f-110">封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c835f-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c835f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c835f-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="c835f-112">My.Application.Log 物件</span><span class="sxs-lookup"><span data-stu-id="c835f-112">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="c835f-113">My.Log 物件</span><span class="sxs-lookup"><span data-stu-id="c835f-113">My.Log Object</span></span>](../../visual-basic/language-reference/objects/my-log-object.md)
