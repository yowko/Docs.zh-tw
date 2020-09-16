---
title: 服務：每秒的安全性驗證和驗證失敗數
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: f6dbf7f6da208bde3a9a380d50fd6caf68576f25
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535907"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>服務：每秒的安全性驗證和驗證失敗數
計數器名稱：每秒的安全性驗證和驗證失敗。  
  
## <a name="description"></a>描述  
 每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。 這類問題包括：  
  
- 無法從訊息中讀取用戶端權杖。  
  
- 用戶端權杖已經驗證失敗 (例如密碼錯誤)。  
  
- 簽章驗證已經失敗 (例如訊息遭到竄改)。  
  
- 此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。  
  
- 發生解密失敗。  
  
- 訊息中遺失某些必要的項目 (例如遺失時間戳記或加密的資料區塊)。  
  
- 在 TLSNEGO/SPNEGO 交換期間發生錯誤。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式計算的：  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
