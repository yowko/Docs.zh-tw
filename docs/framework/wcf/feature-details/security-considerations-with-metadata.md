---
title: 中繼資料的安全性考量
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: 2e1ad9f3c7d2a77ec6237bf1fc12c0d1a67181ad
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411909"
---
# <a name="security-considerations-with-metadata"></a>中繼資料的安全性考量
當 Windows Communication Foundation (WCF) 中使用的中繼資料功能，請考慮發行、 擷取和使用服務中繼資料的安全性含意。  
  
## <a name="when-to-publish-metadata"></a>發行中繼資料的時機  
 根據預設，WCF 服務不要發佈中繼資料。 若要發佈的 WCF 服務中繼資料您必須明確啟用中繼資料發行中繼資料端點新增至您的服務 (請參閱[中繼資料發行](../../../../docs/framework/wcf/feature-details/publishing-metadata.md))。 停用中繼資料發行則會降低服務的攻擊面，並降低非預期資料暴露的風險。 不是所有服務都必須發行中繼資料。 如果您不需要發行中繼資料，可以考慮關閉這個功能。 請注意，仍然可以直接從您使用的服務組件產生中繼資料和用戶端程式碼[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 如需使用 Svcutil.exe 來匯出中繼資料的詳細資訊，請參閱[How to:使用 Svcutil.exe 來匯出編譯的服務程式碼的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)。  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>使用安全繫結發行中繼資料  
 WCF 會提供不安全的預設中繼資料繫結也允許匿名存取中繼資料。 WCF 服務發行服務中繼資料包含有關服務的詳細的描述，並可能有意或無意包含敏感資訊。 例如，服務中繼資料可能包含原意不是要公開廣播的基礎結構作業的相關資訊。 若要防止未經授權存取服務中繼資料，您可以在中繼資料端點中使用安全繫結。 中繼資料端點會回應至使用 Secure Sockets Layer (SSL) 來確保中繼資料安全的 HTTP/GET 要求。 如需詳細資訊，請參閱[如何：確保中繼資料端點的安全](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)。  
  
 確保中繼資料端點的安全同樣能對要求者提供一種方法，可安全地擷取服務中繼資料而避免遇到竄改或詐騙等風險。  
  
## <a name="using-only-trusted-metadata"></a>僅使用信任的中繼資料  
 您可以使用服務中繼資料以自動建構呼叫服務時所需的執行階段元件。 您也可以在設計階段時使用中繼資料以開發用戶端應用程式，或在執行階段時使用以更新用戶端用來呼叫服務的繫結。  
  
 如果以不安全的方法擷取服務中繼資料，就可能遭到竄改或詐騙。 被竄改的中繼資料會將您的用戶端重新導向至惡意服務，其中並包含有害的安全性設定或惡意 XML 結構。 中繼資料文件可能很大，並經常會儲存至檔案系統。 若要防止竄改和詐騙，請在具有安全繫結的情況下使用安全繫結來要求服務中繼資料。  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>使用安全技術來處理中繼資料  
 將會使用標準化通訊協定 (例如 WS-MetadataExchange (MEX))，透過網路經常從服務擷取服務中繼資料。 許多中繼資料格式包括可指向其他中繼資料的參考機制。 
  <xref:System.ServiceModel.Description.MetadataExchangeClient> 型別會自動為您處理 Web 服務描述語言 (WSDL) 文件、XML 結構描述和 MEX 文件中的參考。 從擷取的中繼資料所建立的 <xref:System.ServiceModel.Description.MetadataSet> 物件大小，則會直接與使用之 <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> 執行個體的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 值成比例，也與該 `MaxReceivedMessageSize` 執行個體已使用的繫結 <xref:System.ServiceModel.Description.MetadataExchangeClient> 值成比例。 根據案例的要求，將這些配額設定為適當的值。  
  
 在 WCF 中，服務中繼資料會當做 XML 處理。 而在處理 XML 文件時，應用程式應該自我保護不會受到惡意 XML 結構的攻擊。 使用<xref:System.Xml.XmlDictionaryReader>與適當的配額時處理 XML，並且也設定了<xref:System.Xml.XmlTextReader.DtdProcessing%2A>屬性設<xref:System.Xml.DtdProcessing.Prohibit>。  
  
 在 WCF 中的中繼資料系統加以擴充，而且可以在應用程式組態檔中註冊中繼資料延伸模組 (請參閱[擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md))。 中繼資料延伸項目可以執行任意程式碼，因此您應該使用適當的存取控制清單 (ACL) 來保護應用程式組態檔，並僅註冊信任的中繼資料延伸項目實作。  
  
## <a name="validating-generated-clients"></a>驗證產生的用戶端  
 從擷取自不受信任來源的中繼資料產生用戶端程式碼時，請驗證產生的用戶端程式碼以確保產生的用戶端會遵照您的用戶端應用程式安全性原則。 您可以使用驗證行為來檢查用戶端繫結上的設定，或以視覺化方式檢查使用工具所產生的程式碼。 如需如何實作驗證行為的用戶端的範例，請參閱 <<c0> [ 用戶端驗證](../../../../docs/framework/wcf/samples/client-validation.md)。  
  
## <a name="protecting-application-configuration-files"></a>保護應用程式組態檔  
 服務的應用程式組態檔可能會控制發行中繼資料的方法以及是否發行中繼資料。 強烈建議您透過適當的存取控制清單 (ACL) 來保護應用程式組態檔，以確保攻擊者無法修改這類設定。  
  
## <a name="see-also"></a>另請參閱
- [如何：確保中繼資料端點的安全](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
- [安全性](../../../../docs/framework/wcf/feature-details/security.md)
