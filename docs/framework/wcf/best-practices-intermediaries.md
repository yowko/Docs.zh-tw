---
title: 最佳做法：媒介
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: d69baae9b4f5851f60d8d1336c40e0d18db8e77d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-intermediaries"></a>最佳做法：媒介
當呼叫媒介時必須務必注意地正確處理錯誤，以確認媒介的服務端通道有正常關閉。  
  
 請考慮下列狀況。 用戶端呼叫之後會呼叫後端服務的媒介。  後端服務未定義錯誤合約，因此，任何由該服務擲回的錯誤將被視為不具型別的錯誤。  後端服務則會擲回<xref:System.ApplicationException>而且 WCF 正常中止服務端通道。 <xref:System.ApplicationException> 呈現為擲回媒介的 <xref:System.ServiceModel.FaultException>。 媒介重新擲回 <xref:System.ApplicationException>。 WCF 將此解譯為由媒介產生之不具型別的錯誤，並轉送至用戶端上。 當接收錯誤之後，媒介與用戶端皆會尋找其用戶端通道之錯誤。 然而，媒介的服務端通道仍然會開啟，因為 WCF 不知道該錯誤是嚴重錯誤。  
  
 此狀況的最佳作法是偵測來自服務的錯誤是否為嚴重錯誤，若是，媒介應尋找其服務端通道之錯誤，如下列程式碼片段所示。  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [WCF 錯誤處理](../../../docs/framework/wcf/wcf-error-handling.md)  
 [指定及處理合約與服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
