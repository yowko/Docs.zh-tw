---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9aa8cdffebb0cdf8b1e8225a394edf78ecf032b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238674"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|4209|  
|關鍵字|WFInstanceStore|  
|層級|錯誤|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示嘗試開啟 SQL 連接時，發生逾時。  
  
## <a name="message"></a>訊息  

 嘗試開啟 SQL 連接時發生逾時。 無法在分配的逾時 %1 內完成作業。 分配給此作業的時間可能是較長逾時的一部分。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|逾時|xs:string|開啟 SQL 連接的逾時值。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
