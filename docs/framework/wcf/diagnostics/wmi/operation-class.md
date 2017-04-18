---
title: "Operation 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Operation 類別
作業  
  
## 語法  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## 方法  
 Operation 類別不會定義任何方法。  
  
## 屬性  
 Operation 類別具有下列屬性：  
  
### Action  
 資料型別：字串  
  
 存取類型：唯讀  
  
 要求訊息的 WS\-Addressing 動作。  
  
### AsyncPattern  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表在服務合約中使用 `Begin` \[open\/close angle brackets\] 與 `End` \[open\/close angle brackets\] 方法組，以非同步方式實作作業。  
  
### Behaviors  
 資料型別：行為陣列  
  
 存取類型：唯讀  
  
 與這個作業有關聯的行為。  
  
### IsCallback  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 當作業是回呼作業時為 True。  
  
### IsInitiating  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表方法是否實作可在伺服器上初始化工作階段的作業。  
  
### IsOneWay  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表作業是否傳回回覆訊息。  
  
### IsTerminating  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表作業是否傳回回覆訊息。  
  
### MethodSignature  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的方法簽章。  
  
### Name  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的名稱。  
  
### ParameterTypes  
 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 作業的參數類型。  
  
### ReplyAction  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的回覆訊息的 SOAP 動作值。  
  
### ReturnType  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的傳回類型。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Description.OperationDescription>