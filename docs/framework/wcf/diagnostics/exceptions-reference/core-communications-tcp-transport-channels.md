---
title: "核心通訊：TCP 傳輸通道"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 198ebe4fee3e36264b684cdef43c4e20d1b36921
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-tcp-transport-channels"></a>核心通訊：TCP 傳輸通道
這個主題會列出 TCP 傳輸通道產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|指定之通訊端的遠端端點，未在指定的分配逾時內產生關閉要求的回應。 可能是遠端端點從接收作業中接收 EOF 訊號 (null) 之後，沒有呼叫 Close。 分配給此作業的時間可能是較長逾時的一部分。|
