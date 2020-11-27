---
title: 1025 - BookmarkScopeInitialized
ms.date: 03/30/2017
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
ms.openlocfilehash: 47b4813c21ef637922117d5adf41b3c907c57f32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275267"
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 - BookmarkScopeInitialized

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1025|  
|關鍵字|WFRuntime|  
|層級|「詳細資訊」|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示已初始化 BookmarkScope。  
  
## <a name="message"></a>訊息  

 已用 ID：'%2' 初始化具有 TemporaryId：'%1' 的 BookmarkScope。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:string|書籤的暫時 ID。|  
|InitializedId|xs:string|書籤的初始化 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
