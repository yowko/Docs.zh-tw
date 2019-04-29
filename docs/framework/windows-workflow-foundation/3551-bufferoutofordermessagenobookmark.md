---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755528"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|3551|  
|關鍵字|WFServices|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 表示書籤繼續執行失敗。 當服務執行個體準備好處理這個特定作業時，就會再次嘗試緩衝接收作業。  
  
## <a name="message"></a>訊息  
 目前無法在服務執行個體 '%1' 上執行作業 '%2'。 將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|作業的名稱。|  
|ServiceInstanceId|xs:string|服務執行個體的 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
