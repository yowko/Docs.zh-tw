---
title: 服務：發生錯誤的呼叫數
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: f0c50f4296003f9e1be579ac0901a989f4ce2f04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474678"
---
# <a name="service-calls-faulted"></a>服務：發生錯誤的呼叫數
計數器名稱：發生錯誤的呼叫數。  
  
## <a name="description"></a>描述  
 針對已傳回錯誤之此服務的呼叫數。 Windows Communication Foundation (WCF) 應用程式中，服務方法通訊使用 SOAP 錯誤訊息的處理錯誤資訊。 SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。 由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。  
  
## <a name="see-also"></a>另請參閱  
 [指定及處理合約與服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
