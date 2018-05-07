---
title: 無法取得記錄檔的資料流
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 3f5ac83e6957d6d5883bf5ab191e2a922c874df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>無法取得記錄檔的資料流
無法取得記錄檔的資料流。 根據的檔名\<名稱 > 已在使用中。  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>類別無法建立新的記錄檔，因為所有潛在的記錄檔名稱為基礎\<名稱 > 已在使用中。  
  
 記錄檔太多可能表示應用程式發生架構問題。 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別的文件。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> 或 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> ，以在記錄檔名稱中包括日期戳記。  
  
2.  封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
