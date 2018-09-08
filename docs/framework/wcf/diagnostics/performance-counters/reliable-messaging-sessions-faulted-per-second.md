---
title: 每秒發生錯誤的可信賴傳訊工作階段數
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187120"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a>每秒發生錯誤的可信賴傳訊工作階段數
計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  
 在此服務每秒發生的可信賴傳訊工作階段錯誤數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
