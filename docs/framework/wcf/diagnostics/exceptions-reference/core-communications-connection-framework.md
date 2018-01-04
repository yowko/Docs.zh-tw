---
title: "核心通訊：連線架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713788f8938e43f3516edd95646fc6dc653a56c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="core-communications-connection-framework"></a>核心通訊：連線架構
本主題會列出 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 連線架構產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|CloseTimedOut|Close 方法在指定的時間之後逾時。 請增加傳遞至 Close 呼叫的逾時值，或是增加繫結上的 CloseTimeout 值。 分配給此作業的時間可能是較長逾時的一部分。|  
|ContentTypeMismatch|指定的內容型別已傳送至預期指定項目的服務。 用戶端與服務繫結可能不相符。|  
|DuplexChannelAbortedDuringOpen|指定項目的雙工通道在開啟過程中已被終止。|  
|FramingValueNotAvailable|無法存取值，因為尚未完全解碼。|  
|OperationAbortedDuringConnectionEstablishment|建立與指定項目的連線時作業終止。|  
|ReceiveTimedOut2|接收作業在指定的時間之後逾時。 分配給此作業的時間可能是較長逾時的一部分。|  
|SendCannotBeCalledAfterCloseOutputSession|呼叫 CloseOutputSession 之後，無法在通道上傳送訊息。|
