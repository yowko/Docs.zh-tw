---
title: 未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 5575b108353e9c434ff01e76edc127e8691f0bf4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276122"
---
# <a name="security-calls-not-authorized"></a>未授權的安全性呼叫數

計數器名稱：未授權的安全性呼叫數。  
  
## <a name="description"></a>描述  

 當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。 這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。
