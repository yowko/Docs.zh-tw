---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: ca1f4244fb1a5144cb2d86eaacb9b31137d317c2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275332"
---
# <a name="1022---startbookmarkworkitem"></a>1022 - StartBookmarkWorkItem

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1022|  
|關鍵字|WFRuntime|  
|層級|「詳細資訊」|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示 BookmarkWorkItem 開始執行。  
  
## <a name="message"></a>訊息  

 開始執行活動 ' %1 '、DisplayName： ' %2 '、InstanceId： ' %3 ' 的 BookmarkWorkItem。  BookmarkName：%4、BookmarkScope：%5。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|活動|xs:string|活動的型別名稱。|  
|DisplayName|xs:string|活動的顯示名稱。|  
|InstanceId|xs:string|活動的執行個體 ID。|  
|BookmarkName|xs:string|書籤的名稱。|  
|BookmarkScope|xs:string|書籤的範圍。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
