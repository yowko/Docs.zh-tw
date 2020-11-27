---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: bd3e7539922e6c430c4ffe5bd96ef1ac7dbd098f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261159"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|3552|  
|關鍵字|配額、WFServices|  
|層級|警告|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 表示已達到節流 'MaxPendingMessagesPerChannel' 限制。  
  
## <a name="message"></a>訊息  

 已達到 '%1' 的節流 'MaxPendingMessagesPerChannel' 限制。 若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|限制|xs:string|已達到 MaxPendingMessagesPerChannel 節流的限制。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
