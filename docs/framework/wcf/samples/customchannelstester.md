---
title: CustomChannelsTester
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 802d501dabbf14d30a26cd682afb366f0a83a17a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester` 工具，可以用來針對預先定義之服務合約集合測試自訂通道實作。 您可以選擇服務合約集合，然後將該集合使用 XML 檔傳遞到此工具。 接著，此工具就會產生服務，以及會在訊息交換期間執行自訂通道實作的用戶端。  
  
### <a name="to-build-the-tool"></a>建置工具  
  
1.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
2.  建置此方案會產生三個檔案：CustomChannelsTester.exe、TestSpec.xml 和 SampleRun.cmd。 檔案 SampleRun.cmd 已經示範如何使用此工具來測試範例命令列[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。  
  
### <a name="to-run-the-tool"></a>執行工具  
  
-   在命令提示字元中輸入下列命令：  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     這時必須使用 `/binding` 選項。  
  
     如果 "binding" 不是 `/dll` 提供的系統提供繫結，就需要 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 選項。  
  
     `/testspec` 是選擇項。  
  
     這個選項會根據測試規格和繫結建立伺服器與用戶端。  
  
     執行用戶端與伺服器，然後傳回結果。  
  
     下列是測試規格之描述的範例 XML (testspec.xml)：  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>   
    <!-- Test a sessionful / sessionless contract-->      
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->      
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the CLient. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>      
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
  
## <a name="see-also"></a>另請參閱
