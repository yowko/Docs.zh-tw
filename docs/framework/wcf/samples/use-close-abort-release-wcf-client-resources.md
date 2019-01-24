---
title: 使用關閉和中止發行 WCF 用戶端資源
description: Dispose 可以失敗，而且網路失敗時擲回例外狀況。 這可能導致不想要的行為。 相反地，使用關閉並釋放用戶端的資源，網路失敗時中止。
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 4996ccba955d7946bb76b8124b8b28d803b6f3e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736425"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>關閉和中止網路連線已卸除時，安全地釋放資源
此範例示範如何使用`Close`和`Abort`方法，以清除資源，使用具類型的用戶端時。 `using`陳述式會不穩定的網路連線時，會導致例外狀況。 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務。 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例會說明兩個當 C# "using" 陳述式使用於具型別用戶端時發生的常見問題，並示範在例外狀況之後正確進行清除的程式碼。  
  
 C# "using" 陳述式會產生對 `Dispose`() 的呼叫。 這就跟呼叫 `Close`() 一樣，可能會在發生網路錯誤時擲回例外狀況。 因為對 `Dispose`() 的呼叫會隱含地發生在 "using" 區塊的右邊大括號，所以撰寫和閱讀程式碼的人可能都不會注意到這個例外狀況來源。 這代表應用程式錯誤的潛在來源。  
  
 要在 `DemonstrateProblemUsingCanThrow` 方法中說明的第一個問題，是右大括號會擲回例外狀況，而且右大括號之後的程式碼不會執行：  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 即使在 using 區塊中沒有任何程式碼擲回例外狀況，或是已攔截到 using 區塊內的所有例外狀況，但 `Console.Writeline` 可能仍然不執行，這是因為右大括號所隱含的 `Dispose`() 呼叫可能擲回了例外狀況。  
  
 要在 `DemonstrateProblemUsingCanThrowAndMask` 方法中說明的第二個問題，則是右大括號的另一個會擲回例外狀況的隱含動作：  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 因為 `Dispose`() 會在 "finally" 區塊內發生，如果 `ApplicationException`() 失敗，則永遠無法在 using 區塊之外見到 `Dispose`。 如果區塊外面的程式碼必須知道 `ApplicationException` 何時發生，"using" 建構便可能因為遮罩了這個例外狀況而造成問題。  
  
 最後，範例會在 `DemonstrateCleanupWithExceptions` 中示範如何於例外狀況發生時正確清除。 這段程式碼會使用 try/catch 區塊，報告錯誤並呼叫 `Abort`。 請參閱[預期的例外狀況](../../../../docs/framework/wcf/samples/expected-exceptions.md)攔截例外狀況，從用戶端呼叫的更多詳細的範例。  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  使用陳述式和 ServiceHost:許多自我裝載的應用程式執行稍有多個裝載服務，，而 servicehost.close 則很少會擲回例外狀況，因此這類應用程式可以安全地使用 using 陳述式搭配 ServiceHost。 但是要注意，ServiceHost.Close 可能擲回 `CommunicationException`，因此，如果應用程式會在關閉 ServiceHost 之後繼續執行，您應該避免使用 using 陳述式，而要遵循前述的模式。  
  
 當您執行範例時，作業回應和例外狀況會顯示在用戶端主控台視窗中。  
  
 用戶端處理序將執行三個案例，其中每一個都會嘗試呼叫 `Divide`。 第一個案例示範因 `Dispose`() 發生例外狀況而略過程式碼的情況。 第二個案例示範因 `Dispose`() 發生例外狀況而遮罩了重要例外狀況的情況。 第三個案例則示範進行正確清除。  
  
 從用戶端處理序產生的預期輸出如下：  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>另請參閱
