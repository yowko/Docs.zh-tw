---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774409"
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|39458|  
|關鍵字|WFTracking|  
|層級|警告|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示追蹤記錄已被截斷。 變數/標註/使用者資料已移除。  
  
## <a name="message"></a>訊息  
 已將截斷的追蹤記錄 %1 寫入提供者 %2 的 ETW 工作階段。 變數/附註/使用者資料已移除  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|追蹤記錄號碼。|  
|ProviderId|xs:string|ETW 提供者 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
