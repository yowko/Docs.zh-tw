---
title: 作法：使用服務 Moniker 搭配中繼資料交換合約
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 194caf6a48e64a4358a77ecd514dda456cc35e0b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265956"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>作法：使用服務 Moniker 搭配中繼資料交換合約

在開發新的 WCF 服務之後，您可能會決定要能夠從腳本或 Visual Basic 6.0 應用程式呼叫這些服務。 其中一個方法是產生 WCF 用戶端元件、向 COM 註冊元件、將元件安裝在 GAC 中，然後從您的 Visual Basic 程式碼中參考 COM 類型。 當您散發應用程式時，您也必須散發 WCF 用戶端元件。 然後使用者必須向 COM 註冊 WCF 用戶端組件，並將它放在 GAC 中。 WCF COM Interop 也可讓您進行相同的服務呼叫，而不需要依賴 WCF 用戶端元件。 WCF 標記可讓您從任何 COM 相容的語言呼叫任何 WCF 服務 (Visual Basic、VBScript、Visual Basic for Applications (VBA) 等) ，方法是指定中繼資料交換 (端點 URI，讓服務的標記用來解壓縮服務的類型資訊。 本主題說明如何使用指定 Mex 端點的 WCF 標記來呼叫消費者入門 WCF 範例。  
  
> [!NOTE]
> WCF 用戶端元件所定義的類型絕不會真正具現化。 此組件僅用於中繼資料。  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>使用含有 Mex 位址的服務 Moniker  
  
1. 建立消費者入門範例，並使用 Internet Explorer 流覽至 () 的 URL， `http://localhost/ServiceModelSamples/Service.svc` 以確保服務正常運作。  
  
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
    > 您正在呼叫的服務必須公開 Mex 端點，Moniker 才能從服務讀取中繼資料。 如需詳細資訊，請參閱 [如何：使用設定檔發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。  
  
    > [!NOTE]
    > 如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。  如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
## <a name="see-also"></a>另請參閱

- [作法：使用 Windows Communication Foundation 服務 Moniker 且不註冊](use-the-wcf-service-moniker-without-registration.md)
- [作法：使用服務 Moniker 搭配 WSDL 合約](how-to-use-a-service-moniker-with-wsdl-contracts.md)
