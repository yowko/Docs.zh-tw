---
title: 服務：未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: eb0f0d3e3005a4efca27ec3a63e2a854f735258b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472195"
---
# <a name="service-security-calls-not-authorized"></a>服務：未授權的安全性呼叫數
計數器名稱：未授權的安全性呼叫數。  
  
## <a name="description"></a>描述  
 當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。 這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。
