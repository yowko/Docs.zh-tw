---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|1031|  
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
|例外狀況|xs:string|例外狀況的例外狀況詳細資料|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
