---
title: 404 - ResumeSignpostEvent
ms.date: 03/30/2017
ms.assetid: 395cc7ca-f35f-4295-be97-39a077f99c97
ms.openlocfilehash: 258e2f7e4b9dc1025461519593204c196bf6f415
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33467467"
---
# <a name="404---resumesignpostevent"></a>404 - ResumeSignpostEvent
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|404|  
|關鍵字|疑難排解|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此活動會標記端對端活動的繼續執行。 其中包含了活動的名稱。  
  
## <a name="message"></a>訊息  
 活動界限。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|延伸資料|`xs:string`|活動名稱。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
