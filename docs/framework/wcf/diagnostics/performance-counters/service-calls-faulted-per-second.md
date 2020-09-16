---
title: 服務：每秒發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 211240d5bef7fe31a36f636313b48a2b9e15b239
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556007"
---
# <a name="service-calls-faulted-per-second"></a>服務：每秒發生錯誤的呼叫數
計數器名稱：每秒發生錯誤的呼叫數  
  
## <a name="description"></a>描述  
 每秒傳回至此服務的錯誤呼叫數。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 在 Windows Communication Foundation (WCF) 應用程式中，服務方法會使用 SOAP 錯誤訊息來溝通處理錯誤資訊。 SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。 由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。  
  
## <a name="see-also"></a>另請參閱

- [指定與處理合約和服務中的錯誤](../../specifying-and-handling-faults-in-contracts-and-services.md)
