---
title: 無法取得記錄檔的資料流
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 887356fac3abe5c9d28751f7c4d3b1908ed35acb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078381"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="82bb8-102">無法取得記錄檔的資料流</span><span class="sxs-lookup"><span data-stu-id="82bb8-102">Unable to obtain a stream for the log</span></span>

<span data-ttu-id="82bb8-103">無法取得記錄檔的資料流。</span><span class="sxs-lookup"><span data-stu-id="82bb8-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="82bb8-104">基於的可能檔案名 \<name> 已在使用中。</span><span class="sxs-lookup"><span data-stu-id="82bb8-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="82bb8-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>類別無法建立新的記錄檔，因為根據的所有可能記錄檔名稱 \<name> 都已在使用中。</span><span class="sxs-lookup"><span data-stu-id="82bb8-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="82bb8-106">記錄檔太多可能表示應用程式發生架構問題。</span><span class="sxs-lookup"><span data-stu-id="82bb8-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="82bb8-107">如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="82bb8-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="82bb8-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="82bb8-108">To correct this error</span></span>  
  
1. <span data-ttu-id="82bb8-109">請將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> 或 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> ，以在記錄檔名稱中包括日期戳記。</span><span class="sxs-lookup"><span data-stu-id="82bb8-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="82bb8-110">封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="82bb8-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82bb8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82bb8-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="82bb8-112">我的應用程式 .Log</span><span class="sxs-lookup"><span data-stu-id="82bb8-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="82bb8-113">DirectoryPath。</span><span class="sxs-lookup"><span data-stu-id="82bb8-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
