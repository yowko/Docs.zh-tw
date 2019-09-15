---
title: HOW TO：使用服務 Moniker 搭配中繼資料交換合約
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: e114bc2c046ba7145a91121ce23c82912680a048
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968954"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>HOW TO：使用服務 Moniker 搭配中繼資料交換合約
在開發一些新的 WCF 服務之後，您可能會決定要能夠從腳本或 Visual Basic 6.0 應用程式呼叫這些服務。 其中一個方法是產生 WCF 用戶端元件、向 COM 註冊元件、在 GAC 中安裝元件，然後從您的 Visual Basic 程式碼參考 COM 類型。 當您散發應用程式時，也必須散發 WCF 用戶端元件。 然後使用者必須向 COM 註冊 WCF 用戶端組件，並將它放在 GAC 中。 WCF COM Interop 也可讓您在不依賴 WCF 用戶端元件的情況下，進行相同的服務呼叫。 WCF 標記可讓您藉由指定服務標記用來解壓縮類型的中繼資料交換（Mex）端點 URI，從任何 COM 相容語言（Visual Basic、VBScript、Visual Basic for Applications （VBA）等等）呼叫任何 WCF 服務。服務的相關資訊。 本主題描述如何使用指定 Mex 端點的 WCF 標記來呼叫消費者入門 WCF 範例。  
  
> [!NOTE]
> WCF 用戶端元件所定義的類型實際上不會具現化。 此組件僅用於中繼資料。  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>使用含有 Mex 位址的服務 Moniker  
  
1. 建立消費者入門範例，並使用 Internet Explorer 流覽至其 URL （ http://localhost/ServiceModelSamples/Service.svc) 以確保服務正常運作。  
  
2. 建立 Visual Basic 指令碼或含有下列程式碼的 Visual Basic 應用程式：  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. 執行 Visual Basic 應用程式或指令碼。  
  
    > [!NOTE]
    > 您正在呼叫的服務必須公開 Mex 端點，Moniker 才能從服務讀取中繼資料。 如需詳細資訊，請參閱[如何：使用設定檔](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)發佈服務的中繼資料。  
  
    > [!NOTE]
    > 如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。  如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
## <a name="see-also"></a>另請參閱

- [如何：使用 Windows Communication Foundation 服務的名字標記而不進行註冊](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [如何：搭配 WSDL 合約使用服務標記](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
