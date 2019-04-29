---
title: 核心通訊：TCP 傳輸通道
ms.date: 03/30/2017
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
ms.openlocfilehash: 0dfbf939b39d53f104d749e0c0d24e04a05185e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929918"
---
# <a name="core-communications-tcp-transport-channels"></a>核心通訊：TCP 傳輸通道
這個主題會列出 TCP 傳輸通道產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|指定之通訊端的遠端端點，未在指定的分配逾時內產生關閉要求的回應。 可能是遠端端點從接收作業中接收 EOF 訊號 (null) 之後，沒有呼叫 Close。 分配給此作業的時間可能是較長逾時的一部分。|
