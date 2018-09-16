---
title: 每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664445"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>每秒捨棄的可信賴傳訊訊息數
計數器名稱：每秒捨棄的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  
 在此服務中已捨棄的每秒可信賴傳訊訊息總數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
