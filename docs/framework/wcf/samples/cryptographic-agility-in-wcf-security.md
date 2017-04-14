---
title: "WCF 安全性中的加密彈性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# WCF 安全性中的加密彈性
本範例示範如何在標準\/自訂演算法中指定，以便在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端和服務中提供敏捷的密碼編譯實作。  此範例是由下列專案所組成：  
  
 服務  
 這是自我裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，會實作 `ICalculator` 介面，並且使用 <xref:System.ServiceModel.WsHttpBinding> 在停用安全工作階段與可靠工作階段的情況下保護端點的安全。  這項服務會定義自訂的 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。  
  
 用戶端  
 這是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，會在驗證成功之後存取服務。  它會叫用由 `ICalculator` 介面公開並且由服務實作的作業。  這個用戶端還會定義相同的自訂 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。  
  
### 若要使用這個範例  
  
1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟 CryptoAgility.sln 方案。  
  
2.  按下 CTRL\+SHIFT\+B 以建置方案。  
  
3.  開啟 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 並巡覽至 \\WCF\\Basic\\Security\\CryptoAgility\\Service\\bin 目錄，然後以滑鼠右鍵按一下 service.exe 並選取 \[**以系統管理員身分執行**\]，以系統管理員權限執行 service.exe 檔。  
  
4.  巡覽至 \\WCF\\Basic\\Security\\CryptoAgility\\Client\\bin 目錄，並正常執行 client.exe 檔。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。  請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[適用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。  此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## 請參閱  
 [安全性](../../../../docs/framework/wcf/feature-details/security.md)