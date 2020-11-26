---
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: 903071e7b1f89dc3489b8d3ac05427d699a33a7e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240754"
---
# <a name="3507---serviceendpointadded"></a>3507 - ServiceEndpointAdded

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|3507|  
|關鍵字|WFServices|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 表示已加入服務端點。  
  
## <a name="message"></a>訊息  

 已經針對位址 '%1'、繫結 '%2' 和合約 '%3' 加入服務端點。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|位址|xs:string|端點的位址。|  
|繫結|xs:string|端點的繫結。|  
|合約|xs:string|端點的合約。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
