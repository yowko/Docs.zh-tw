---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|1029|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示已排定 FaultWorkItem。  
  
## <a name="message"></a>訊息  
 FaultWorkItem 已排定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。  活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|錯誤活動的型別名稱。|  
|FaultActivityDisplayName|xs:string|錯誤活動的顯示名稱。|  
|FaultActivityInstanceId|xs:string|錯誤活動的執行個體 ID。|  
|ExceptionActivity|xs:string|擲回例外狀況之活動的型別名稱。|  
|ExceptionActivityDisplayName|xs:string|擲回例外狀況之活動的顯示名稱。|  
|ExceptionActivityInstanceId|xs:string|擲回例外狀況之活動的執行個體 ID。|  
|例外狀況|xs:string|例外狀況的例外狀況詳細資料|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
