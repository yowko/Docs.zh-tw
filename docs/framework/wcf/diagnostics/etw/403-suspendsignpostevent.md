---
title: 403 - SuspendSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee1daab843ad0a2161d13b86bcd657b7236ddaa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="403---suspendsignpostevent"></a>403 - SuspendSignpostEvent
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|403|  
|關鍵字|疑難排解|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此活動會標記端對端活動的暫停。 其中包含了活動的名稱。  
  
## <a name="message"></a>訊息  
 活動界限。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|延伸資料|`xs:string`|活動名稱。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
