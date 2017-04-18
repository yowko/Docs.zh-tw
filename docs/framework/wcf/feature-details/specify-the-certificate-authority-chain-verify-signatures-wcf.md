---
title: "HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "憑證 [WCF], 指定憑證授權單位憑證鏈結"
  - "憑證 [WCF], 驗證簽章"
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)
當 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 收到透過 X.509 憑證簽署的 SOAP 訊息時，根據預設會確認 X.509 憑證是由受信任的憑證授權單位所發行。它會搜尋憑證存放區並判斷該憑證授權單位的憑證是否已指定為受信任來完成所有程序。為了讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 做出正確的判斷，憑證授權單位憑證鏈結必須安裝在正確的憑證存放區。  
  
### 若要安裝憑證授權單位憑證鏈結  
  
-   針對 SOAP 訊息收件者賴以信任 X.509 憑證的每個原始憑證授權單位，將憑證授權單位憑證鏈結安裝到憑證存放區 \(已設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 為可從其中擷取 X.509 憑證\)。  
  
     例如，如果 SOAP 訊息收件者想要信任由 Microsoft 所發行的 X.509 憑證，則必須將 Microsoft 的憑證授權單位憑證鏈結安裝到憑證存放區 \(已設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 從其中搜尋 X.509 憑證\)。您可以在程式碼或組態中指定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會從其中搜尋 X.509 憑證的憑證存放區。例如，您可以使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法或在組態中，以下列幾種方式 \(包括 [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)\) 在程式碼中進行指定。  
  
     由於 Windows 在產品出貨時，預設會附上由受信任憑證授權單位所發行的憑證鏈結，您可能不需要針對所有憑證授權單位安裝其憑證鏈結。  
  
    1.  匯出憑證授權單位憑證鏈結。  
  
         每個憑證授權單位將有不同的執行方式。如果憑證授權單位執行 Microsoft 憑證服務，請選取 \[**下載 CA 憑證，憑證鏈結或 CRL**\]，然後選擇 \[**下載 CA 憑證**\]。  
  
    2.  匯入憑證授權單位憑證鏈結。  
  
         在 Microsoft Management Console \(MMC\) 中，開啟 \[憑證\] 嵌入式管理單元。針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 已設定為從中擷取 X.509 憑證的憑證存放區，選取 \[**受信任的根** **憑證授權單位**\] 資料夾。在 \[**受信任的根憑證授權單位**\] 資料夾中，以滑鼠右鍵按一下 \[**憑證**\] 資料夾，然後指向 \[**所有工作**\]，接著按一下 \[**匯入**\]。提供在步驟 a 中匯出的檔案。  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 透過 MMC 使用憑證嵌入式管理單元的詳細資訊，請參閱 [HOW TO：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。  
  
## 請參閱  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)