---
title: "Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor"
apilocation: 
  - "Microsoft.VisualStudio.Activities.dll"
apitype: "Assembly"
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
建立 [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) 類別的執行個體。  
  
## 語法  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
  
```  
  
#### 參數  
  
## 參數值  
 *operationDescription*  
  
 描述要在產生之工作流程活動中執行的作業，包括作業名稱、傳回型別和參數資訊。  此參數的值不能為 **null**。  它應描述會使用訊息合約並接收含有一則訊息之引數的同步作業。  如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
 *configurationName*  
  
 指定端點組態名稱。  此參數的值不能為 **null** 或是空的。  如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
 *proxyNamespace*  
  
 指定作業的服務命名空間。  此參數的值不能為 **null** 或是空的。  如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
## 請參閱  
 [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)