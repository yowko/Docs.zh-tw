---
title: 每秒的安全性驗證和驗證失敗數
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 546d81b73e912915d265fb194de4ad9e45d55cea
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163913"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>每秒的安全性驗證和驗證失敗數
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
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算：  
  
 (N1-N0)/((D1-D0)/F)
