---
title: "延伸 WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c84f25dfd5d3066f9c5d0b62bc0b28bc98c283d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extending-wcf"></a>延伸 WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 允許您修改及延伸執行階段元件，以精確控制及延伸服務應用程式。 本節中的主題將深入說明延伸性結構。 如需基本程式設計的詳細資訊，請參閱[基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [擴充 ServiceHost 與服務模型層](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 服務模型層負責從基礎通道提取傳入訊息，將它們以應用程式碼轉譯成方法叫用，然後將結果傳回給呼叫者。  服務模型延伸會修改或實作涉及發送器功能、自訂行為、訊息與參數攔截與其他延伸性功能的執行或通訊行為與功能。  
  
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 繫結是描述連接至端點所需之通訊詳細資料的物件。 繫結延伸或自訂繫結會實作支援應用程式功能所需的自訂通訊功能。  
  
 [擴充通道層](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 通道層位於服務模型層之下，負責用戶端和服務之間的訊息交換。 通道延伸可以實作新的通訊協定功能，例如安全性。 通道延伸也會傳輸功能，例如實作新的網路傳輸以傳送 SOAP 訊息。  
  
 [擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的安全性是由傳輸安全性 (完整性、機密性和驗證)、存取控制 (授權) 和稽核所組成。 `IdentityModel` 命名空間中的類別是由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用於存取控制。 瞭解安全性結構可讓您建立自訂宣告類型，以配合自訂存取控制系統。  
  
 [擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中繼資料系統是一個由類別和介面組成的群組，代表實作服務應用程式所需的中繼資料。 修改或擴充類別，或是實作和設定介面，即可匯出和匯入自訂中繼資料 (例如 Web 服務描述語言 (WSDL) 擴充功能或自訂 WS-PolicyAttachments 判斷提示)。  
  
 [擴充編碼器與序列化程式](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 編碼器和序列化程式會將資料從一種形式轉譯為另一種形式。 本節中的主題將說明如何延伸所提供的類別，以符合特殊需求。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>相關章節  
 [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [WCF 功能詳細資料](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [方針及最佳做法](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
