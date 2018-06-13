---
title: 服務：每秒發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 86eddc62fb9aec8eced49ae70865583f3a50eb85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474096"
---
# <a name="service-calls-faulted-per-second"></a>服務：每秒發生錯誤的呼叫數
計數器名稱：每秒發生錯誤的呼叫數  
  
## <a name="description"></a>描述  
 每秒傳回至此服務的錯誤呼叫數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Windows Communication Foundation (WCF) 應用程式中，服務方法通訊使用 SOAP 錯誤訊息的處理錯誤資訊。 SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。 由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。  
  
## <a name="see-also"></a>另請參閱  
 [指定及處理合約與服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
