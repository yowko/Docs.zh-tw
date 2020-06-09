---
title: 中繼資料格式
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a74a57843beaba09b969678a34cad3ad8bed7050
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598836"
---
# <a name="metadata-formats"></a>中繼資料格式
Windows Communication Foundation （WCF）支援下表中的元資料格式。  
  
## <a name="metadata-specifications-and-usage"></a>中繼資料規格和用法  
  
|通訊協定|規格和用法|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web 服務描述語言 (WSDL) 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF 使用 Web 服務描述語言（WSDL）來描述服務。|  
|XML 結構描述|[XML 架構第2部分：資料類型第二版](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/)和[XML 架構第1部分：結構第二版](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF 會使用 XML 架構來描述訊息中使用的資料類型。|  
|WS 原則|[Web 服務原則 1.2 - 架構 (WS-Policy)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Web 服務原則 1.5 - 架構](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF 使用 WS-Policy 1.2 或1.5 規格搭配特定領域的判斷提示，來描述服務需求和功能。|  
|WS 原則附件|[Web 服務原則 1.2 - 附件 (WS-PolicyAttachment)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF 會執行 WS-Policy 附件，以在 WSDL 中的各種範圍附加原則運算式。|  
|WS 中繼資料交換|[Web 服務中繼資料交換 (WS-MetadataExchange) 1.1 版](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF 會執行透過 ws-metadataexchange，以取得 XML 架構、WSDL 和 WS 原則。|  
|WSDL 的 WS 定址繫結|[Web 服務定址 1.0 - WSDL 繫結](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF 會執行 WSDL 的 WS-ADDRESSING 系結，以便在 WSDL 中附加定址資訊。|  
  
## <a name="see-also"></a>請參閱

- [系統提供的互通性繫結所支援的 Web 服務通訊協定](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL 與原則](wsdl-and-policy.md)
