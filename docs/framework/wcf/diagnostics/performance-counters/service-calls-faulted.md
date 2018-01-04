---
title: "服務：發生錯誤的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5f37f3befba7a3dfdce50869aaea0033ed74aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-faulted"></a>服務：發生錯誤的呼叫數
計數器名稱：發生錯誤的呼叫數。  
  
## <a name="description"></a>描述  
 針對已傳回錯誤之此服務的呼叫數。 在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中，服務方法使用 SOAP 錯誤訊息來溝通處理錯誤資訊。 SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。 由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。  
  
## <a name="see-also"></a>請參閱  
 [指定及處理合約與服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
