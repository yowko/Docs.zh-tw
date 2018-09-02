---
title: 每秒佇列捨棄的訊息數
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418244"
---
# <a name="queue-dropped-messages-per-second"></a>每秒佇列捨棄的訊息數
計數器名稱：每秒捨棄的佇列訊息。  
  
## <a name="description"></a>描述  
 此服務的佇列傳輸每秒捨棄的訊息數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
