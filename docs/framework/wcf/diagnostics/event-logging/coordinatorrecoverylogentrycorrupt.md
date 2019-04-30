---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: faf4a07badb71588c601cd9390e4d8e3f187e629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969646"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a>CoordinatorRecoveryLogEntryCorrupt
識別碼:139  
  
 嚴重性：錯誤  
  
 類別：TransactionBridge  
  
## <a name="description"></a>描述  
 此事件表示協調器修復記錄項目損毀，且無法還原序列化。 這個錯誤可能會造成資料遺失。 事件會列出異動識別碼、修復資料 (以 Base64 編碼)、例外狀況、處理序名稱和處理序識別碼。  
  
## <a name="see-also"></a>另請參閱

- [事件記錄](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [事件一般參考](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
