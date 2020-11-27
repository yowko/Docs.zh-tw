---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 4a4979047481687ef0d5c9d5891dec8f2826beed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263655"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 - TransactedReceiveScopeEndCommitFailed

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|3557|  
|關鍵字|WFServices|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 表示呼叫 CommittableTransaction 上的 EndCommit 擲回 TransactionException。  
  
## <a name="message"></a>訊息  

 呼叫 ID = '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|TransactionId|xs:string|CommittableTransaction 的 ID。|  
|例外狀況|xs:string|例外狀況的例外狀況詳細資料|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
