---
title: 中繼資料格式
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 01f0d7a2212b2af7e2d3a959ed91624edec46ce8
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720461"
---
# <a name="metadata-formats"></a>元資料格式

Windows Communication Foundation (WCF) 支援下表中的元資料格式。  
  
## <a name="metadata-specifications-and-usage"></a>中繼資料規格和用法  
  
|通訊協定|規格和用法|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web 服務描述語言 (WSDL) 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF 會使用 Web 服務描述語言 (WSDL) 來描述服務。|  
|XML 結構描述|[XML 架構第2部分：資料類型第二版](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) 及 [XML 架構第1部分：結構第二版](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF 會使用 XML 架構來描述訊息中使用的資料類型。|  
|WS 原則|[Web 服務原則 1.2 - 架構 (WS-Policy)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Web 服務原則 1.5 - 架構](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF 會使用 WS-原則1.2 或1.5 規格搭配網域特定的判斷提示，以描述服務需求和功能。|  
|WS 原則附件|[Web 服務原則 1.2 - 附件 (WS-PolicyAttachment)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF 會執行 WS 原則附件，以在 WSDL 中的不同範圍附加原則運算式。|  
|WS 中繼資料交換|[Web 服務中繼資料交換 (WS-MetadataExchange) 1.1 版](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF 會實透過 ws-metadataexchange 來取得 XML 架構、WSDL 和 WS 原則。|  
|WSDL 的 WS 定址繫結|[Web 服務定址 1.0 - WSDL 繫結](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF 會在 wsdl 中實址的 WS-ADDRESSING 系結，以附加定址資訊。|  
  
## <a name="see-also"></a>另請參閱

- [系統提供的互通性繫結所支援的 Web 服務通訊協定](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL 與原則](wsdl-and-policy.md)
