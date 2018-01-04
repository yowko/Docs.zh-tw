---
title: "永久性雙工"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1298f150709b48f18de654be2ab17adfdcbf42a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="durable-duplex"></a>永久性雙工
這個範例示範如何透過 [!INCLUDE[wf](../../../../includes/wf-md.md)] 的訊息活動來設定永久性的雙工訊息交換。 永久性的雙工訊息交換是長時間進行的雙向訊息交換。 此訊息交換的存留期間可能比通訊通道的存留期間以及服務執行個體的記憶體中存留期間還要長。  
  
## <a name="sample-details"></a>範例詳細資料  
 在這個範例中，設定兩個透過 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 實作的 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] 服務，來進行永久性的雙工訊息交換。 永久性雙工訊息交換由兩個單向訊息透過 MSMQ 傳送並使用相互關聯[.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059)。 訊息是使用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive> 訊息活動來傳送。 .NET Context Exchange 用來在傳送的訊息上指定回呼位址。 兩個服務是透過使用 Windows Process Activation Services (WAS) 所主控，並設定為啟用服務執行個體的持續性。  
  
 第一個服務 (Service1.xamlx) 會傳送要求給傳送服務 (Service2.xamlx)，使其做些工作。 一旦工作完成，Service2.xamlx 會傳回通知給 Service1.xamlx，表示工作已完成。 工作流程主控台應用程式會設定這些服務接聽的佇列，並傳送初始開始訊息以啟動 Service1.xamlx。 一旦 Service1.xamlx 從 Service2.xamlx 收到所要求工作已完成的通知，Service1.xamlx 會將結果儲存至 XML 檔案。 在等候回呼訊息時，Service1.xamlx 會使用預設 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> 保存其執行個體狀態。 Service2.xamlx 會在完成 Service1.xamlx 所要求工作的過程中保存其執行個體狀態。  
  
 若要設定服務以透過 MSMQ 使用 .NET Context Exchange，這兩個服務應設定為使用包含 <xref:System.ServiceModel.Channels.ContextBindingElement> 和 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement> 的自訂繫結。 回呼位址是以 <xref:System.ServiceModel.Channels.ContextBindingElement> 來指定，包含在所有透過自訂繫結傳送之訊息的回呼內容標頭中。 下列程式碼範例定義此自訂繫結。  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  這個範例所使用的繫結並不安全。 當您部署應用程式時，應該根據應用程式的安全性需求來設定繫結。  
  
> [!NOTE]
>  這個範例所使用的佇列不是異動式。 如需範例，示範如何設定[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]訊息交換使用交易佇列中，請參閱[MSMQ 啟用](../../../../docs/framework/wcf/samples/msmq-activation.md)範例。  
  
 由 Service1.xamlx 傳送至 Service2.xamlx 的訊息是透過設定有 Service2.xamlx 位址和先前定義之自訂繫結的用戶端端點所傳送。 從 Service2.xamlx 到 Service1.xamlx 的回呼是透過不含明確設定之位址的用戶端端點所傳送，因為位址是取自 Service1.xamlx 所傳送的回呼內容。 下列程式碼範例定義用戶端端點。  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 下列程式碼範例將 net.msmq 基底位址的預設通訊協定對應變更為使用此自訂繫結，藉以公開使用此自訂繫結的端點。  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 下列程式碼範例將 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 行為加入至兩個服務，並指定持續性資料庫的連接字串，藉以啟用兩個服務的持續性。  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a>系統需求  
 本範例需要下列元件。  
  
1.  Internet Information Services。  
  
2.  Internet Information Services -> IIS 6.0 管理相容性 -> IIS Metabase 及 IIS 6.0 設定相容性。  
  
3.  全球資訊網服務 -> 應用程式開發功能 -> ASP.NET。  
  
4.  Microsoft Message Queues (MSMQ) 伺服器。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  設定持續性資料庫和結果目錄。  
  
    1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
    2.  巡覽至這個範例的資料夾，並執行 Setup.cmd。  
  
2.  設定虛擬應用程式。  
  
    1.  從 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元，執行下列命令註冊 ASP.NET。  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  執行[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以管理員權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]，然後選取**系統管理員身分執行**。  
  
    3.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 DurableDuplex.sln 檔案。  
  
3.  設定服務佇列。  
  
    1.  若要執行 DurableDuplex 用戶端，按下 F5。  
  
    2.  開啟**電腦管理**主控台執行`Compmgmt.msc`從命令提示字元。  
  
    3.  展開**服務和應用程式**，**訊息佇列**。 **私用佇列**。  
  
    4.  以滑鼠右鍵按一下 durableduplex/service1.xamlx 和 durableduplex/service2.xamlx 佇列，並選取**屬性**。  
  
    5.  選取**安全性**索引標籤上，並允許**Everyone 接收訊息**，**查看訊息**和**傳送訊息**這兩個佇列的權限。  
  
    6.  開啟 Internet Information Services (IIS) 管理員。  
  
    7.  瀏覽至**伺服器**，**網站**， **Default Web site**，**私人**，**永久性雙工**選取**進階選項**。  
  
    8.  變更**啟用的通訊協定**至**http，net.msmq**。  
  
4.  執行範例。  
  
    1.  瀏覽至 http://localhost/private/durableduplex/service1.xamlx 和 http://localhost/private/durableduplex/service2.xamlx，以確保兩個服務執行中。  
  
    2.  按下 F5，執行 DurableDuplexClient。  
  
         當永久性雙工訊息交換完成時，result.xml 檔案會儲存至 C:\Inbox 資料夾，這個檔案包含訊息交換結果。  
  
#### <a name="to-cleanup-optional"></a>若要清除 (選擇性)  
  
1.  執行 Cleanup.cmd。  
  
    1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
    2.  巡覽至這個範例的資料夾，並執行 Cleanup.cmd。  
  
2.  移除服務的虛擬應用程式。  
  
    1.  開啟 網際網路資訊服務 (IIS) 管理員執行`Inetmgr.exe`從命令提示字元。  
  
    2.  瀏覽至預設的網站，並移除**私人**虛擬目錄。  
  
3.  移除此範例中設定的佇列。  
  
    1.  開啟 [電腦管理] 主控台執行`Compmgmt.msc`從命令提示字元。  
  
    2.  展開**服務和應用程式**，**訊息佇列**，**私用佇列**。  
  
    3.  刪除 durableduplex/service1.xamlx 和 durableduplex/service2.xamlx 佇列。  
  
4.  移除 C:\Inbox 目錄。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`