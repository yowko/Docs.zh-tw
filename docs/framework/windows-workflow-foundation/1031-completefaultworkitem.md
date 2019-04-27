---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008794"
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1031|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示 FaultWorkItem 已完成。  
  
## <a name="message"></a>訊息  
 已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。 活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|錯誤活動的型別名稱。|  
|FaultActivityDisplayName|xs:string|錯誤活動的顯示名稱。|  
|FaultActivityInstanceId|xs:string|錯誤活動的執行個體 ID。|  
|ExceptionActivity|xs:string|擲回例外狀況之活動的型別名稱。|  
|ExceptionActivityDisplayName|xs:string|擲回例外狀況之活動的顯示名稱。|  
|ExceptionActivityInstanceId|xs:string|擲回例外狀況之活動的執行個體 ID。|  
|例外|xs:string|例外狀況的例外狀況詳細資料|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
