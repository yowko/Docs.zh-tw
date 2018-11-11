---
title: 端點：每秒的安全性驗證和驗證失敗數
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: 43886f79585fb9a63eeb51360cc869365c100a1d
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744232"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>端點：每秒的安全性驗證和驗證失敗數
計數器名稱：每秒的安全性驗證和驗證失敗數  
  
## <a name="description"></a>描述  
 每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。 這類問題包括：  
  
-   無法從訊息中讀取用戶端權杖。  
  
-   用戶端權杖已經驗證失敗 (例如密碼錯誤)。  
  
-   簽章驗證已經失敗 (例如訊息遭到竄改)。  
  
-   此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。  
  
-   發生解密失敗。  
  
-   訊息中遺失某些必要的項目 (例如遺失時間戳記或加密的資料區塊)。  
  
-   在 TLSNEGO/SPNEGO 交換期間發生錯誤。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，其值會計算公式如下：  
  
 (N1-N0)/((D1-D0)/F)
