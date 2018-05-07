---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|4203|  
|關鍵字|WFInstanceStore|  
|層級|錯誤|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示因為已超過鎖定期限或已刪除鎖定擁有人，所以 SQL 提供者無法延長鎖定期限。 SqlWorkflowInstanceStore 即將中止。  
  
## <a name="message"></a>訊息  
 無法延長鎖定期限，已超過鎖定期限或已刪除鎖定擁有人。 正在中止 SqlWorkflowInstanceStore。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
