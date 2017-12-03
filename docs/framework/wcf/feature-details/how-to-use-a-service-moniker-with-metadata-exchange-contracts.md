---
title: "HOW TO：使用服務 Moniker 搭配中繼資料交換合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31720b0639f9be68a2124b4ff844a2837787ef81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>HOW TO：使用服務 Moniker 搭配中繼資料交換合約
在開發一些新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之後，您可能會決定想要能夠從指令檔或 Visual Basic 6.0 應用程式來呼叫這些服務。 有一種方法會產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件，請向 COM 註冊組件，在 GAC 中安裝組件，然後從您的 Visual Basic 程式碼參照 COM 型別。 當您散發應用程式時，也必須散發 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件。 然後使用者必須向 COM 註冊 WCF 用戶端組件，並將它放在 GAC 中。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] COM Interop 也讓您不需依賴 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件，就可以進行相同的服務呼叫。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker 可讓您藉由指定服務 Moniker 用於擷取有關服務之型別資訊的中繼資料交換 (Mex) 端點 URI，從與 COM 相容的語言 (Visual Basic、VBScript、Visual Basic for Applications (VBA) 等等) 呼叫任何 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。 本主題將說明如何使用指定 Mex 端點的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker 來呼叫「使用者入門」[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。  
  
> [!NOTE]
>  由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件定義的型別實際上永遠不會產生。 此組件僅用於中繼資料。  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>使用含有 Mex 位址的服務 Moniker  
  
1.  請建置「使用者入門」範例，並使用 Internet Explorer 瀏覽至其 URL (http://localhost/ServiceModelSamples/Service.svc)，以確保服務正在運作。  
  
2.  建立 Visual Basic 指令碼或含有下列程式碼的 Visual Basic 應用程式：  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  執行 Visual Basic 應用程式或指令碼。  
  
    > [!NOTE]
    >  您正在呼叫的服務必須公開 Mex 端點，Moniker 才能從服務讀取中繼資料。 如需詳細資訊，請參閱[How to： 使用組態檔的服務發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。  
  
    > [!NOTE]
    >  如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。  如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 使用 Windows Communication Foundation 服務 Moniker，但不註冊](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [如何： 使用服務 Moniker 搭配 WSDL 合約](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
