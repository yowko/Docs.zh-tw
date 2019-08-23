---
title: 預期的例外狀況
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 7611b070df31b7a0997a94c07594716ee264af5e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961600"
---
# <a name="expected-exceptions"></a>預期的例外狀況
此範例示範如何在使用型別用戶端時，攔截預期的例外狀況。 這個範例是以執行計算機服務的[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此範例示範正確的程式必須處理的兩個預期例外狀況類型之捕捉與處理方式：`TimeoutException` 和 `CommunicationException`。  
  
 從 Windows Communication Foundation (WCF) 用戶端上的通訊方法所擲回的例外狀況可能是預期的或非預期的。 未預期的例外狀況包含 `OutOfMemoryException` 之類的災難性失敗，以及像 `ArgumentNullException` 或 `InvalidOperationException` 之類的程式設計錯誤。 通常沒有任何實用的方式可以處理未預期的錯誤, 因此在呼叫 WCF 用戶端通訊方法時, 通常不應該攔截它們。  
  
 WCF 用戶端上通訊方法的預期例外狀況`TimeoutException`包括`CommunicationException`、和的`CommunicationException`任何衍生類別。 這表示通訊期間發生問題, 可透過中止 WCF 用戶端並回報通訊失敗來安全地處理。 因為外部因素可能導致在任何應用程式中發生這些錯誤，正確的應用程式必須捕捉這些例外狀況，並在發生時加以復原。  
  
 用戶端可以擲回的 `CommunicationException` 衍生類別有好幾種。 在某些情況中，應用程式也會捕捉當中的一些狀況以進行特殊處理，但同時讓其他狀況當成 `CommunicationException` 來處理。 首先您可以捕捉比較特別的例外狀況類型，然後在稍後的 catch 子句中捕捉 `CommunicationException` 來做同樣的處理。  
  
 可呼叫用戶端通訊方法的程式碼必須捕捉 `TimeoutException` 和 `CommunicationException`。 處理此類錯誤的一種方式，就是中止用戶端並報告通訊失敗。  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 如果發生預期的例外狀況，日後用戶端可能還能使用，也可能無法使用。 若要判斷用戶端是否仍可使用，請檢查 `State` 屬性是否設為 `CommunicationState`.Opened。 如果仍為開啟狀態，表示仍可使用。 否則，您應該中止用戶端，並釋放所有用戶端的參考。  
  
> [!CAUTION]
>  您可以發現，具有工作階段的用戶端通常在發生例外狀況後無法繼續使用，而不具有工作階段的用戶端卻常常在發生例外狀況後還能使用。 但是，這兩種情況並不必然發生，因此假如您想要在發生例外狀況後繼續使用用戶端，則您的應用程式應該檢查 `State` 屬性以確定用戶端仍為開啟狀態。  
  
 當您執行範例時，作業回應和例外狀況會顯示在用戶端主控台視窗中。  
  
 用戶端處理序會執行兩個案例，每一個都會嘗試呼叫 `Add` 並接著呼叫 `Divide`。 第一個案例會在呼叫 `Divide` 之前，先中止用戶端以便模擬網路問題。 第二個案例會將逾時值設為過短導致方法無法完成，以造成逾時情況。 從用戶端處理序產生的預期輸出如下：  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
