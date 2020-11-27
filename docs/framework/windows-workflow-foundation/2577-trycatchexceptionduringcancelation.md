---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: 33c68984e88eaa5e3028899a7c3066c94a65e8eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271235"
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 - TryCatchExceptionDuringCancelation

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|2577|  
|關鍵字|WFActivities|  
|層級|警告|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示 TryCatch 活動的子活動在取消期間擲回例外狀況。  
  
## <a name="message"></a>訊息  

 TryCatch 活動 '%1' 的子活動在取消期間擲回例外狀況。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|活動的顯示名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
