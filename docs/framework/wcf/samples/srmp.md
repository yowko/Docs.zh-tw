---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183333"
---
# <a name="srmp"></a>SRMP
這個範例示範如何使用訊息佇列 (MSMQ)，透過 HTTP 來執行交易佇列通訊。  
  
 在佇列通訊中，用戶端會使用佇列與服務通訊。 更精確地說，用戶端會傳送訊息至佇列。 服務會接收來自佇列的訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。  
  
 MSMQ 允許使用 HTTP (包括使用 HTTPS) 傳送訊息至佇列。 在此示例中，我們將演示使用 Windows 通信基礎 （WCF） 排隊通信以及如何通過 HTTP 發送消息。 MSMQ 會使用稱為 SRMP 的通訊協定，這是適用在透過 HTTP 進行通訊的 SOAP 通訊協定。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
4. 在 **"添加/刪除 Windows 元件**"中運行示例之前，請確保 MSMQ 已安裝 HTTP 支援。 安裝 HTTP 支援時，會自動安裝網際網路資訊服務 (IIS)，並在 IIS 中為 MSMQ 新增通訊協定支援。  
  
5. 如果您想要確定會在通訊時使用 HTTP，則可以讓 MSMQ 在固定模式中執行。 這可以確保任何訊息都無法使用非 HTTP 傳輸進到電腦上裝載的佇列中。  
  
6. 選擇 MSMQ 在硬化模式下運行後，電腦需要在 Windows Server 2003 上重新開機。  
  
7. 執行服務。  
  
8. 執行該用戶端。 確定您已將端點位址改為指向電腦名稱或 IP 位址，而非指向 localhost。 用戶端便會傳送訊息並結束。  
  
## <a name="requirements"></a>需求  
 若要執行這個範例，除了安裝 MSMQ 之外，還必須在服務及用戶端機器兩端都安裝 IIS。  
  
## <a name="demonstrates"></a>示範  
 該示例演示了使用 MSMQ 通過 HTTP 發送 WCF 排隊消息。 這也會呼叫 SRMP 訊息處理。 傳送佇列訊息時，在傳送端電腦上的 MSMQ 會透過 TCP 或 HTTP 傳輸，將訊息傳輸至接收端佇列管理員。 如果使用者選擇 SRMP，就表示他選擇了 HTTP 做為佇列傳輸的傳輸機制。 SRMP Secure (SRMPS) 會啟用 HTTPS。  
  
## <a name="example"></a>範例  
 此範例程式碼是以交易範例為基礎。 當傳送訊息至佇列以及從佇列接收訊息時，其使用 SRMP 的方式，與使用原生通訊協定傳送和接收訊息的方式相同。  
  
 您可以變更用戶端的組態，指定所選擇的佇列傳輸通訊協定。 佇列傳輸通訊協定可以是原生、SRMP 或 SrmpSecure 的其中一種通訊協定。 根據預設，傳輸通訊協定為「原生」。 在這個範例中，用戶端和服務會在組態中指定使用 SRMP。  
  
 相對於傳輸安全性，SRMP 會有一些限制。 預設的 MSMQ 傳輸安全性需要有 Active Directory，而這會要求傳送端佇列管理員和接收端佇列管理員都必須位於相同的 Windows 網域中。 如果要超越 HTTP 界限傳送訊息，這就變得不可行。 因此，預設的傳輸安全性將無法運作。 如果想要有傳輸安全性，就必須將傳輸安全性設定為憑證， 而您也可以使用訊息安全性來保護訊息的安全性。 在這個範例中，會同時關閉傳輸和訊息安全性，以便於說明 SRMP 訊息處理。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"
           bindingConfiguration="srmpBinding"
           binding="netMsmqBinding"
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 執行範例時會產生下列輸出。  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
