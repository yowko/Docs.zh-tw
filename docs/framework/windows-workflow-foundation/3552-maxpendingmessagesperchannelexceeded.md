---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|3552|  
|關鍵字|配額、WFServices|  
|層級|警告|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 表示已達到節流 'MaxPendingMessagesPerChannel' 限制。  
  
## <a name="message"></a>訊息  
 已達到節流 'MaxPendingMessagesPerChannel' 限制為 '%1'。 若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|限制|xs:string|已達到 MaxPendingMessagesPerChannel 節流的限制。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
