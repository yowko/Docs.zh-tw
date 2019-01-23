---
title: 資料傳輸與序列化
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 5192030fa2eda45431dd8a3765603d3081b93fa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595314"
---
# <a name="data-transfer-and-serialization"></a>資料傳輸與序列化
在連線系統中，服務與用戶端會仰賴資料交換來完成任何工作。 身為開發人員的服務或用戶端中，您也必須了解 Windows Communication Foundation (WCF) 如何處理資料與資料序列化以建立有效率且容易維護的應用程式。  
  
## <a name="in-this-section"></a>本節內容  
 [指定服務合約中的資料傳輸](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 說明在服務中進行資料傳輸的基本概念。  
  
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 說明何謂資料合約以及如何建立與使用它們。  
  
 [資料合約序列化程式](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 說明如何透過 <xref:System.Runtime.Serialization.DataContractSerializer> 類別，或 <xref:System.Runtime.Serialization.XmlObjectSerializer> 類別的任何延伸來完成資料的序列化作業。  
  
 [使用 XmlSerializer 類別](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 說明如何與為何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別 (<xref:System.Runtime.Serialization.DataContractSerializer> 類別的替代項目)。  
  
 [使用訊息合約](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 說明訊息合約如何允許對 SOAP 訊息進行精密控制。  
  
 [使用 Message 類別](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 說明如何使用 Message 類別功能。  
  
 [篩選](../../../../docs/framework/wcf/feature-details/filtering.md)  
 說明可依據不同準則對訊息進行前置處理的篩選功能。  
  
 [大型資料和資料流](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 說明如何傳送大型資料區塊，例如二進位檔。  
  
 [資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 說明在設計資料傳輸與序列化的程式時，要注意的項目。  
  
 [資料傳輸架構概觀](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 說明 WCF 中的資料傳輸的整體設計的檢視。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>相關章節  
 [擴充編碼器與序列化程式](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>另請參閱
- [最佳做法：資料合約版本控制](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [服務版本設定](../../../../docs/framework/wcf/service-versioning.md)
