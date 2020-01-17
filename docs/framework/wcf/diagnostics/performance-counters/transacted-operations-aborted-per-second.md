---
title: 每秒中止的交易作業數
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: d03f1faf7d2a00d02500fe9759ba940445d8eee3
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164017"
---
# <a name="transacted-operations-aborted-per-second"></a>每秒中止的交易作業數
計數器名稱：每秒中止的交易作業數。  
  
## <a name="description"></a>描述  
 此服務中每秒中止的異動作業數。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
