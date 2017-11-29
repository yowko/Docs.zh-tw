---
title: "每秒中止的交易作業數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 96ef8181b95d8614ae6cbfeaa468b0138d1129d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-operations-aborted-per-second"></a>每秒中止的交易作業數
計數器名稱：每秒中止的交易作業數。  
  
## <a name="description"></a>描述  
 此服務中每秒中止的異動作業數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
