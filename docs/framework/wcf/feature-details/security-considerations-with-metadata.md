---
title: 中繼資料的安全性考量
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: c41ebf5c39e74932a4bade610c4e236b28444327
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601019"
---
# <a name="security-considerations-with-metadata"></a>中繼資料的安全性考量
使用 Windows Communication Foundation （WCF）中的中繼資料功能時，請考慮發行、抓取和使用服務中繼資料的安全性影響。  
  
## <a name="when-to-publish-metadata"></a>發行中繼資料的時機  
 WCF 服務預設不會發行中繼資料。 若要發行 WCF 服務的中繼資料，您必須將中繼資料端點新增至您的服務，以明確啟用中繼資料發行（請參閱[發行中繼資料](publishing-metadata.md)）。 停用中繼資料發行則會降低服務的攻擊面，並降低非預期資料暴露的風險。 不是所有服務都必須發行中繼資料。 如果您不需要發行中繼資料，可以考慮關閉這個功能。 請注意，您仍然可以使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)直接從服務元件產生中繼資料和用戶端程式代碼。 如需使用 Svcutil 匯出中繼資料的詳細資訊，請參閱[如何：使用 Svcutil 從已編譯的服務程式代碼匯出中繼資料](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)。  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>使用安全繫結發行中繼資料  
 WCF 提供的預設中繼資料系結並不安全，而且允許匿名存取中繼資料。 WCF 服務發行的服務中繼資料包含有關服務的詳細描述，而且可能會刻意或無意地包含敏感性資訊。 例如，服務中繼資料可能包含原意不是要公開廣播的基礎結構作業的相關資訊。 若要防止未經授權存取服務中繼資料，您可以在中繼資料端點中使用安全繫結。 中繼資料端點會回應至使用 Secure Sockets Layer (SSL) 來確保中繼資料安全的 HTTP/GET 要求。 如需詳細資訊，請參閱[如何：保護中繼資料端點](how-to-secure-metadata-endpoints.md)。  
  
 確保中繼資料端點的安全同樣能對要求者提供一種方法，可安全地擷取服務中繼資料而避免遇到竄改或詐騙等風險。  
  
## <a name="using-only-trusted-metadata"></a>僅使用信任的中繼資料  
 您可以使用服務中繼資料以自動建構呼叫服務時所需的執行階段元件。 您也可以在設計階段時使用中繼資料以開發用戶端應用程式，或在執行階段時使用以更新用戶端用來呼叫服務的繫結。  
  
 如果以不安全的方法擷取服務中繼資料，就可能遭到竄改或詐騙。 被竄改的中繼資料會將您的用戶端重新導向至惡意服務，其中並包含有害的安全性設定或惡意 XML 結構。 中繼資料文件可能很大，並經常會儲存至檔案系統。 若要防止竄改和詐騙，請在具有安全繫結的情況下使用安全繫結來要求服務中繼資料。  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>使用安全技術來處理中繼資料  
 將會使用標準化通訊協定 (例如 WS-MetadataExchange (MEX))，透過網路經常從服務擷取服務中繼資料。 許多中繼資料格式包括可指向其他中繼資料的參考機制。 <xref:System.ServiceModel.Description.MetadataExchangeClient> 型別會自動為您處理 Web 服務描述語言 (WSDL) 文件、XML 結構描述和 MEX 文件中的參考。 從擷取的中繼資料所建立的 <xref:System.ServiceModel.Description.MetadataSet> 物件大小，則會直接與使用之 <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> 執行個體的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 值成比例，也與該 `MaxReceivedMessageSize` 執行個體已使用的繫結 <xref:System.ServiceModel.Description.MetadataExchangeClient> 值成比例。 根據案例的要求，將這些配額設定為適當的值。  
  
 在 WCF 中，服務中繼資料會以 XML 的形式處理。 而在處理 XML 文件時，應用程式應該自我保護不會受到惡意 XML 結構的攻擊。 在 <xref:System.Xml.XmlDictionaryReader> 處理 XML 時使用搭配適當的配額，同時將 <xref:System.Xml.XmlTextReader.DtdProcessing%2A> 屬性設定為 <xref:System.Xml.DtdProcessing.Prohibit> 。  
  
 WCF 中的中繼資料系統可延伸，而且可以在應用程式佈建檔中註冊中繼資料延伸模組（請參閱[擴充中繼資料系統](../extending/extending-the-metadata-system.md)）。 中繼資料延伸項目可以執行任意程式碼，因此您應該使用適當的存取控制清單 (ACL) 來保護應用程式組態檔，並僅註冊信任的中繼資料延伸項目實作。  
  
## <a name="validating-generated-clients"></a>驗證產生的用戶端  
 從擷取自不受信任來源的中繼資料產生用戶端程式碼時，請驗證產生的用戶端程式碼以確保產生的用戶端會遵照您的用戶端應用程式安全性原則。 您可以使用驗證行為來檢查用戶端繫結上的設定，或以視覺化方式檢查使用工具所產生的程式碼。 如需如何執行驗證行為之用戶端的範例，請參閱[用戶端驗證](../samples/client-validation.md)。  
  
## <a name="protecting-application-configuration-files"></a>保護應用程式組態檔  
 服務的應用程式組態檔可能會控制發行中繼資料的方法以及是否發行中繼資料。 強烈建議您透過適當的存取控制清單 (ACL) 來保護應用程式組態檔，以確保攻擊者無法修改這類設定。  
  
## <a name="see-also"></a>請參閱

- [HOW TO：安全中繼資料端點](how-to-secure-metadata-endpoints.md)
- [安全性](security.md)
