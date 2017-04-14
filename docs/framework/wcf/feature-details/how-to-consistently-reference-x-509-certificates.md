---
title: "HOW TO：一律參考 X.509 憑證 | Microsoft Docs"
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
  - "憑證 [WCF], 參考 X.509 憑證"
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# HOW TO：一律參考 X.509 憑證
您可以用幾種方式來識別憑證：依據憑證的雜湊、依據簽發者和序號，或是依據主體金鑰識別元 \(SKI\)。SKI 會提供憑證之主體公開金鑰的唯一識別，而且通常會在使用 XML 數位簽章時使用。SKI 值通常是做為「*X.509 憑證延伸*」\(X.509 Certificate Extension\) 中 X.509 憑證的一部分。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 具有預設的「*參考樣式*」\(Referencing Style\)，此參考樣式會在憑證遺失 SKI 延伸時使用簽發者和序號。如果憑證包含 SKI 延伸，預設的參考樣式便會使用 SKI 來指向憑證。如果在開發應用程式的期間，您從使用不用 SKI 延伸的憑證切換到使用 SKI 延伸的憑證，在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 產生之訊息中所使用的參考樣式也會變更。  
  
 如果無論 SKI 延伸是否存在都必須使用一致的參考樣式，這時就可以設定需要的參考樣式，如下列程式碼所示。  
  
## 範例  
 下列範例會建立自訂的安全性繫結項目，該項目會使用單一的一致參考樣式、簽發者名稱及序號。  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## 編譯程式碼  
 要編譯程式碼時，必須有下列命名空間：  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## 請參閱  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)