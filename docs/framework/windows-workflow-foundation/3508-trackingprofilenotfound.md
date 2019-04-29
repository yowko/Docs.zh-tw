---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755567"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|3508|  
|關鍵字|WFServices|  
|層級|詳細資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 表示在組態檔中找不到 TrackingProfile，或是 ActivityDefinitionId 不符合設定檔。  
  
## <a name="message"></a>訊息  
 找不到 ActivityDefinitionId '%2' 的 TrackingProfile '%1'。 在組態檔中找不到 TrackingProfile，或者 ActivityDefinitionId 不相符。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:string|追蹤設定檔的名稱。|  
|ActivityDefinitionId|xs:string|活動定義 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
