---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774266"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|4209|  
|關鍵字|WFInstanceStore|  
|層級|錯誤|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示嘗試開啟 SQL 連接時，發生逾時。  
  
## <a name="message"></a>訊息  
 嘗試開啟 SQL 連接時發生逾時。 無法在分配的逾時 %1 內完成作業。 分配給此作業的時間可能是較長逾時的一部分。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|逾時|xs:string|開啟 SQL 連接的逾時值。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
