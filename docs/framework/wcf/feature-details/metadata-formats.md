---
title: 中繼資料格式
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a3c6b1f551d1bff8c68a91f33e62df289d2078cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493434"
---
# <a name="metadata-formats"></a>中繼資料格式
Windows Communication Foundation (WCF) 支援下表中的中繼資料格式。  
  
## <a name="metadata-specifications-and-usage"></a>中繼資料規格和用法  
  
|通訊協定|規格和用法|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web 服務描述語言 (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF 會使用 Web 服務描述語言 (WSDL) 來描述服務。|  
|XML 結構描述|[XML 結構描述第 2 部分： 資料類型第二版](http://go.microsoft.com/fwlink/?LinkId=94861)和[XML 結構描述第 1 部分： 結構第二版](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> WCF 會使用 XML 結構描述來描述訊息中所使用的資料類型。|  
|WS 原則|[Web 服務原則 1.2-架構 (Ws-policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Web 服務原則 1.5-架構](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF 使用 Ws-policy 1.2 或 1.5 規格與定義域特定的判斷提示來描述服務需求和功能。|  
|WS 原則附件|[Web 服務原則 1.2-附件 (Ws-policyattachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> WCF 實作 Ws-policy 附件附加原則運算式，在 WSDL 中的各種範圍。|  
|WS 中繼資料交換|[Web 服務中繼資料交換 (Ws-metadataexchange) 1.1 版](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF 實作 Ws-metadataexchange 以擷取 XML 結構描述、 WSDL 和 Ws-policy。|  
|WSDL 的 WS 定址繫結|[Web 服務定址 1.0-WSDL 繫結](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> WCF 實作將以 WSDL 的定址資訊附加至 WSDL 的 Ws-addressing 繫結。|  
  
## <a name="see-also"></a>另請參閱  
 [系統提供的互通性繫結所支援的 Web 服務通訊協定](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL 與原則](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
