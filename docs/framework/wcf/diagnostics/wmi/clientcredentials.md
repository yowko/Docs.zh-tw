---
title: "ClientCredentials | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ClientCredentials
ClientCredentials  
  
## 語法  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## 方法  
 ClientCredentials 類別不會定義任何方法。  
  
## 屬性  
 ClientCredentials 類別具有下列屬性：  
  
### ClientCertificate  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用戶端用來向服務驗證的 X.509 憑證。  
  
### HttpDigest  
 資料型別：字串  
  
 存取類型：唯讀  
  
 目前的 Http 摘要式認證。  
  
### IssuedToken  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用來聯繫本機安全性權杖服務的端點位址與繫結。  
  
### 對等  
 資料型別：字串  
  
 存取類型：唯讀  
  
 對等節點用來向 mesh 中的其他節點驗證自己時使用的認證。  
  
### ServiceCertificate  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務的 X.509 憑證。  
  
### SupportInteractive  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定認證是否支援互動式交涉的布林值。  
  
### UserName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用戶端用來向服務驗證自身的使用者名稱和密碼。  
  
### Windows  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用戶端用來向服務驗證自身的 Windows 認證。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Description.ClientCredentials>