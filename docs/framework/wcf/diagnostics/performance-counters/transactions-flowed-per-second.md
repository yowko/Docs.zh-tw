---
title: 每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927188"
---
# <a name="transactions-flowed-per-second"></a>每秒流動的異動數
計數器名稱：每秒流動的異動數  
  
## <a name="description"></a>描述  
 一秒內流動至此作業的異動數。 每當傳送給作業的訊息中出現交易識別碼時，此計數器就會遞增。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
