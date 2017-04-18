---
title: "CallbackBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# CallbackBehavior
CallbackBehavior  
  
## 語法  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## 方法  
 CallbackBehavior 類別不會定義任何方法。  
  
## 屬性  
 CallbackBehavior 類別具有下列屬性：  
  
### AutomaticSessionShutdown  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 如果是 true，當服務關閉雙工工作階段時會自動關閉該工作階段。  
  
### ConcurrencyMode  
 資料型別：字串  
存取類型：唯讀  
  
 指定服務支援單一執行緒、多重執行緒或可重新進入 \(Reentrant\) 呼叫。  
  
### IgnoreExtensionDataObject  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否要將未知的序列化資料傳送到網路上的值。  
  
### IncludeExceptionDetailInFaults  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 啟用時，回呼上之例外狀況的詳細資料會附加到傳回到服務的錯誤中。  
  
### MaxItemsInObjectGraph  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 已序列化物件中允許的項目數目上限。  
  
### UseSynchronizationContext  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否使用目前的同步化內容來選擇執行的執行緒。  
  
### ValidateMustUnderstand  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定系統或應用程式是否會強制執行 SOAP MustUnderstand 標頭處理。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>