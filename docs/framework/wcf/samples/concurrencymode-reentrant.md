---
title: "ConcurrencyMode Reentrant | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# ConcurrencyMode Reentrant
這個範例示範在服務實作上使用 ConcurrencyMode.Reentrant 的必要性與隱含意義。ConcurrencyMode.Reentrant 意指在指定的時間裡，服務 \(或回呼\) 只會處理一則訊息 \(類似於 `ConcurencyMode.Single`\)。為確保執行緒安全，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會鎖定處理訊息的 `InstanceContext`，使它無法處理任何其他訊息。在 Reentrant 模式的情況下，會在服務即將進行傳出呼叫之前解除鎖定 `InstanceContext` \(因此允許進行後續呼叫，而這個呼叫可能是可重新進入 \(Reentrant\) 的，如範例中所示\)，以便在下次進入服務時取得鎖定。為方便示範行為，範例會顯示用戶端與服務如何使用雙工合約相互傳送訊息。  
  
 所定義的合約是一份雙工合約，其中包含服務所實作的 `Ping` 方法，以及用戶端所實作的 `Pong` 回呼方法。用戶端會使用滴答計數來叫用伺服器的 `Ping` 方法，從而啟始呼叫。服務則會確認滴答計數不等於 0，再叫用回呼方法 `Pong`，並同時遞減滴答計數。其做法如下列範例程式碼所示。  
  
```  
  
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
  
```  
  
 此回呼之 `Pong` 實作的邏輯與 `Ping` 實作的相同。也就是，它會確認滴答計數不為零，然後在回呼通道 \(在本例中，是先前用來傳送原始 `Ping` 訊息的通道\) 上叫用 `Ping` 方法，並將滴答計數遞減 1。一旦滴答計數到達 0，方法就會將所有回覆傳回 \(從而將其包裝解開\) 至啟始呼叫之用戶端所發出的第一項呼叫。其做法如下列回呼實作所示。  
  
```  
  
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
  
```  
  
 `Ping` 和 `Pong` 方法都屬於要求\/回覆模式，意即在 `CallbackChannel<T>.Pong()` 的呼叫傳回之前，對於 `Ping` 的第一項呼叫將不會傳回。在用戶端上，`Pong` 方法要等到它所進行的下一個 `Ping` 呼叫傳回時，才會傳回。因為回呼和服務都必須進行傳出的要求\/回覆呼叫，才能回覆暫止要求，所以必須將這兩個實作標記為 ConcurrencyMode.Reentrant 行為。  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
## 示範  
 若要執行範例，請建置用戶端和伺服器專案，然後開啟兩個命令視窗，再將目錄變更到 \<sample\>\\CS\\Service\\bin\\debug 和 \<sample\>\\CS\\Client\\bin\\debug 目錄。接著，輸入 `service.exe` 以啟動服務，然後再使用當做輸入引數傳遞的滴答計數初始值來叫用 Client.exe。10 次滴答計數的範例輸出如下所示。  
  
```  
  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
  
```  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## 請參閱