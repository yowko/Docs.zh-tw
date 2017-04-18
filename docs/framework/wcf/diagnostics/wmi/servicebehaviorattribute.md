---
title: "ServiceBehaviorAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## 語法  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## 方法  
 ServiceBehaviorAttribute 類別不會定義任何方法。  
  
## 屬性  
 ServiceBehaviorAttribute 類別具有下列屬性：  
  
### AutomaticSessionShutdown  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否要在用戶端關閉輸出工作階段時自動關閉工作階段。  
  
### ConcurrencyMode  
 資料型別：字串  
存取類型：唯讀  
  
 代表服務支援單一執行緒、多重執行緒或可重新進入 \(Reentrant\) 呼叫。  
  
### ConfigurationName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務組態的名稱。  
  
### IgnoreExtensionDataObject  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否要將未知的序列化資料傳送到網路上的值。  
  
### IncludeExceptionDetailInFaults  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否要針對偵錯用途，在傳回給用戶端的 SOAP 錯誤詳細資料中包含 Managed 例外狀況資訊。  
  
### InstanceContextMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定何時建立新的服務物件。  
  
### MaxItemsInObjectGraph  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 已序列化物件中允許的項目數目上限。  
  
### Name  
 資料型別：字串  
  
 存取類型：唯讀  
  
 WSDL 格式的服務名稱屬性。  
  
### 命名空間  
 資料型別：字串  
  
 存取類型：唯讀  
  
 WSDL 格式的服務目標命名空間。  
  
### ReleaseServiceInstanceOnTransactionComplete  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否會在目前的交易完成時回收服務物件。  
  
### TransactionAutoCompleteOnSessionClose  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定當目前的工作階段關閉時，是否會完成暫止的交易。  
  
### TransactionIsolationLevel  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定交易隔離等級。  
  
### TransactionTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 交易必須完成的期間。  
  
### UseSynchronizationContext  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否使用目前的同步化內容來選擇執行緒執行。  
  
### ValidateMustUnderstand  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定系統或應用程式是否會強制執行 SOAP MustUnderstand 標頭處理。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>