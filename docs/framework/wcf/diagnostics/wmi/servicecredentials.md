---
title: "ServiceCredentials | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceCredentials
ServiceCredentials  
  
## 語法  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## 方法  
 ServiceCredentials 類別不會定義任何方法。  
  
## 屬性  
 ServiceCredentials 類別有下列屬性：  
  
### ClientCertificate  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用戶端憑證驗證與此服務的佈建設定。  
  
### IssuedTokenAuthentication  
 資料型別：字串  
  
 存取類型：唯讀  
  
 這項服務目前發行的權杖驗證設定。  
  
### 對等  
 資料型別：字串  
  
 存取類型：唯讀  
  
 目前的認證驗證與對等傳輸端點將使用的佈建設定。  
  
### SecureConversationAuthentication  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定目前的安全對話設定。  
  
### ServiceCertificate  
 資料型別：字串  
  
 存取類型：唯讀  
  
 與這項服務關聯的憑證。  
  
### UserNameAuthentication  
 資料型別：字串  
  
 存取類型：唯讀  
  
 這項服務的使用者名稱和密碼設定。  
  
### WindowsAuthentication  
 資料型別：字串  
  
 存取類型：唯讀  
  
 這項服務的 Windows 驗證設定。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Description.ServiceCredentials>