---
title: 無法寫入記錄檔，因為如果寫入，會使它超過 MaximumSize 值
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 28a4b9286b13f8c7c72c4e98871846c2ca265aa9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619787"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="00b1e-102">無法寫入記錄檔，因為如果寫入，會使它超過 MaximumSize 值</span><span class="sxs-lookup"><span data-stu-id="00b1e-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>
<span data-ttu-id="00b1e-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別無法寫入記錄檔，因為：</span><span class="sxs-lookup"><span data-stu-id="00b1e-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="00b1e-104">記錄檔大小 (以位元組為單位) 大於 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> 屬性的值</span><span class="sxs-lookup"><span data-stu-id="00b1e-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="00b1e-105">—且—</span><span class="sxs-lookup"><span data-stu-id="00b1e-105">—and—</span></span>  
  
- <span data-ttu-id="00b1e-106"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> 屬性的值是 <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>。</span><span class="sxs-lookup"><span data-stu-id="00b1e-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00b1e-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="00b1e-107">To correct this error</span></span>  
  
1. <span data-ttu-id="00b1e-108">封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="00b1e-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="00b1e-109">變更 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> 屬性的值以允許較大的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="00b1e-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="00b1e-110">將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> ，以在記錄檔太大時，捨棄訊息而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="00b1e-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b1e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00b1e-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="00b1e-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="00b1e-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="00b1e-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="00b1e-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
