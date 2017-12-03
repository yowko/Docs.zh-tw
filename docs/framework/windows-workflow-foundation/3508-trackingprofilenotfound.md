---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 346cb98b1285883a9a85f2c7abb6147f42734395
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|3508|  
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
