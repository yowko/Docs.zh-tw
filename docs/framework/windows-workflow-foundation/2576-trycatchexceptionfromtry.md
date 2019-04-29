---
title: 2576 - TryCatchExceptionFromTry
ms.date: 03/30/2017
ms.assetid: 47e48973-b17c-4a16-8338-c84b54aa0a6e
ms.openlocfilehash: cdc48a1a08e997f7bc6a0ad6b93aa13640af9ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755645"
---
# <a name="2576---trycatchexceptionfromtry"></a>2576 - TryCatchExceptionFromTry
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|2576|  
|關鍵字|WFActivities|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示 TryCatch 活動攔截到例外狀況。  
  
## <a name="message"></a>訊息  
 TryCatch 活動 '%1' 攔截到型別 '%2' 的例外狀況。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|活動的顯示名稱。|  
|例外|xs:string|例外狀況的型別名稱。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
