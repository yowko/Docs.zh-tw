---
title: PiiLoggingNotAllowed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c96da5fe16c468e6ba4dedcdf377c23ba437f47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="piiloggingnotallowed"></a>PiiLoggingNotAllowed
識別碼：108  
  
 嚴重性：錯誤  
  
 分類：追蹤  
  
## <a name="description"></a>描述  
 這個事件表示沒有在記錄任何已知的 PII。 記錄已知的 PII 是不允許的。 若要允許記錄已知的 PII，請將 Machine.config 中的 "enableLoggingKnownPii" 設定為 `true`。此事件會列出處理序名稱和處理序識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [事件記錄](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [事件一般參考](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
