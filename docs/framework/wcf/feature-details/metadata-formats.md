---
title: "中繼資料格式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a>中繼資料格式
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 支援下表中的中繼資料格式。  
  
## <a name="metadata-specifications-and-usage"></a>中繼資料規格和用法  
  
|通訊協定|規格和用法|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web 服務描述語言 (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 Web 服務描述語言 (WSDL) 來描述服務。|  
|XML 結構描述|[XML 結構描述第 2 部分： 資料類型第二版](http://go.microsoft.com/fwlink/?LinkId=94861)和[XML 結構描述第 1 部分： 結構第二版](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 XML 結構描述來說明訊息中使用的資料型別。|  
|WS 原則|[Web 服務原則 1.2-架構 (Ws-policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Web 服務原則 1.5-架構](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將 WS-Policy 1.2 或 1.5 規格與定義域特定的判斷提示一起使用，以描述服務需求和功能。|  
|WS 原則附件|[Web 服務原則 1.2-附件 (Ws-policyattachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 實作 WS-Policy 附件以便在不同的 WSDL 範圍中附加原則運算式。|  
|WS 中繼資料交換|[Web 服務中繼資料交換 (Ws-metadataexchange) 1.1 版](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 實作 WS-MetadataExchange 以擷取 XML 結構描述、WSDL 和 WS-Policy。|  
|WSDL 的 WS 定址繫結|[Web 服務定址 1.0-WSDL 繫結](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 實作 WSDL 的 WS-Addressing 繫結，以便將定址資訊附加到 WSDL。|  
  
## <a name="see-also"></a>另請參閱  
 [Web 服務系統提供的互通性繫結所支援的通訊協定](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL 和原則](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
