---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 4bb76a93ec7a07a735def1f1d5dc79decb7792ad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239830"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|1006|  
|關鍵字|WFRuntime|  
|層級|錯誤|  
|通路|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  

 表示工作流程應用程式發生未處理的例外狀況。  
  
## <a name="message"></a>訊息  

 WorkflowInstance 識別碼： ' %1 ' 發生未處理的例外狀況。  例外狀況源自活動 ' %2 '、DisplayName： ' %3 '。  將採取下列動作： %4。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|工作流程的執行個體 ID。|  
|例外狀況|`xs:string`|例外狀況的例外狀況詳細資料|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
