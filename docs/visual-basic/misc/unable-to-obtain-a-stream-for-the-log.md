---
title: 無法取得記錄檔的資料流
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 540ff3fbba72d33b2efaa58ad7a8019628f5e83f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344750"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>無法取得記錄檔的資料流
無法取得記錄檔的資料流。 可能的檔案名稱，根據\<名稱 > 已被使用。  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>類別無法建立新的記錄檔，因為所有的記錄檔名稱將會根據\<名稱 > 已被使用。  
  
 記錄檔太多可能表示應用程式發生架構問題。 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別的文件。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> 或 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> ，以在記錄檔名稱中包括日期戳記。  
  
2. 封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
