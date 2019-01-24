---
title: 每秒發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: dd35e4096ab4e2740c638903975af085b01a1fbf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640117"
---
# <a name="calls-faulted-per-second"></a>每秒發生錯誤的呼叫數
計數器名稱：每秒發生錯誤的呼叫數  
  
## <a name="description"></a>描述  
 每秒將錯誤傳回至此作業的呼叫數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 在 Windows Communication Foundation (WCF) 應用程式，服務方法通訊，使用 SOAP 錯誤訊息的處理錯誤資訊。 SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。 由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。  
  
## <a name="see-also"></a>另請參閱
- [指定及處理合約與服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
