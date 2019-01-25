---
title: PiiLoggingNotAllowed
ms.date: 03/30/2017
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
ms.openlocfilehash: 4df8a9cae517baff99f7fb47047a3dd275c63524
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592649"
---
# <a name="piiloggingnotallowed"></a>PiiLoggingNotAllowed
識別碼:108  
  
 嚴重性：錯誤  
  
 類別：追蹤  
  
## <a name="description"></a>描述  
 這個事件表示沒有在記錄任何已知的 PII。 記錄已知的 PII 是不允許的。 若要允許記錄已知的 PII，請將 Machine.config 中的 "enableLoggingKnownPii" 設定為 `true`。此事件會列出處理序名稱和處理序識別碼。  
  
## <a name="see-also"></a>另請參閱
- [事件記錄](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [事件一般參考](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
