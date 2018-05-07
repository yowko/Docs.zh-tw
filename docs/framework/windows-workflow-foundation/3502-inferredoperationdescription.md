---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|3502|  
|關鍵字|WFServices|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 表示已從 WorkflowService 推斷出 OperationDescription。  
  
## <a name="message"></a>訊息  
 已從 WorkflowService 推斷出合約 '%2' 中 Name='%1' 的 OperationDescription。 IsOneWay=%3。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|作業的名稱。|  
|ContractName|xs:string|合約的名稱。|  
|IsOneWay|xs:string|True 或 False 表示合約是否為單向。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
