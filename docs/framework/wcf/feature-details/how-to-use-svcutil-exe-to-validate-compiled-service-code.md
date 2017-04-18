---
title: "HOW TO：使用 Svcutil.exe 來驗證已編譯服務程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：使用 Svcutil.exe 來驗證已編譯服務程式碼
您可以使用[ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 來偵測服務實作和組態中的錯誤，而不需要裝載服務。  
  
### 若要驗證服務  
  
1.  將服務編譯為可執行檔以及一或多個相依組件。  
  
2.  開啟 SDK 命令提示字元  
  
3.  在命令提示字元中，使用下列格式啟動 Svcutil.exe 工具。  如需各種參數的詳細資訊，請參閱 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 主題的＜服務驗證＞一節。  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     您必須使用 `/serviceName` 選項以指出您要驗證的服務組態名稱。  
  
     `assemblyPath` 引數會指定服務的可執行檔和一或多個組件的路徑，而這些組件中含有要驗證的服務類型。  可執行組件必須具有相關聯的組態檔，才能提供服務組態。  您可以使用標準命令列萬用字元來提供多個組件。  
  
## 範例  
 下列命令會執行在 myServiceHost.exe 可執行檔中實作的服務 myServiceName。  將會自動載入服務的組態檔 \(myServiceHost.exe.config\)。  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## 請參閱  
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)