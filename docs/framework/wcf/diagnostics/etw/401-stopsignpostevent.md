---
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 1776252c362feb3c3ebc04651603944040ceee7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="401--stopsignpostevent"></a>401- StopSignPostEvent
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|401|  
|關鍵字|疑難排解|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此事件會標記端對端活動的結束。 其中包含了活動的名稱。  
  
## <a name="message"></a>訊息  
 活動界限。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|延伸資料|`xs:string`|活動名稱。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
