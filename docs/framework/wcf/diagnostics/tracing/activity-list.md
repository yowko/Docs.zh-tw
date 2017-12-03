---
title: "活動清單"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c3b478d88eff022d8cb28f4123291f4662644ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="activity-list"></a>活動清單
本主題將列出所有由 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 定義的活動。  
  
> [!NOTE]
>  您也可以使用程式設計方式來定義活動，以便將使用者追蹤加以群組。 如需詳細資訊，請參閱[發出使用者程式碼追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)。  
  
## <a name="servicemodel-activities"></a>ServiceModel 活動  
 下表列出主要使用方式案例的所有活動。  
  
|標籤|活動名稱|活動類型|描述|  
|-----------|-------------------|-------------------|-----------------|  
|A、M|環境活動|N/A (此活動非由 ServiceModel 控制)|在任何 ServiceModel 程式碼的呼叫 (用戶端或伺服器端) 之前，於 TLS 內設定其識別碼的活動。<br /><br /> 範例：在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 用戶端上呼叫而開啟，或呼叫 serviceHost.open 而開啟的活動。|  
|B|建構<br /><br /> ChannelFactory。 ContractType：‘[Type]’。|建構||  
|C|開啟<br /><br /> [ClientBase &#124;ChannelFactory]。 ContractType：‘[Type]’。|開啟||  
|I|關閉 [ClientBase &#124;ChannelFactory]。 ContractType：‘[Type]’。|關閉||  
|M|建構 ServiceHost。 ServiceType：‘[Type]’。|建構||  
|N|開啟 ServiceHost。 ServiceType：‘[Type]’。|開啟||  
|Z|關閉 ServiceHost。 ServiceType：‘[Type]’。|關閉||  
|O|在 ‘[address]’ 接聽。|ListenAt|這個活動和下一個活動是傳輸特有的。 ListenAt 活動代表對應至通道接聽程式正在接聽之位址的內容。 在 MSMQ 中，則因為佇列對應至一個位址，所以這個活動代表佇列本身。 在連線導向的傳輸下，這個活動會接聽傳入連線，若為 MSMQ，則會接聽 MSMQ 訊息。 這個活動是在 ServiceHost.Open() 期間建立，其中會包含建立及處置接聽項的相關追蹤，以及向外傳輸至所有 ReceiveBytes 活動的相關追蹤。|  
|P|在連線 ‘[address]’ 接收位元組。 接收 MSMQ 訊息。|ReceiveBytes|在這個活動中，資料最後會取得已處理的 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 訊息。 在連線導向傳輸或 http 的情形下，會等待傳入位元組。 對於 TCP/具名管道，此活動的存留期就是連線的存留期，因為它是在建立連線時建立的。 如果是 http，此活動的存留期會是訊息要求的存留期，並且會在訊息傳送時建立。 這個活動包含建立及處置連線的相關追蹤 (如果有的話)，並且會向外傳輸至所有訊息 (物件) 處理活動。<br /><br /> 在 MSMQ 的情況下，則會是擷取 MSMQ 訊息的活動。|  
|Q|處理訊息 [number]  (注意，[number] 是從 1 開始，依序遞增的值)。|ProcessMessage|處理傳入訊息。 這個活動會在收到的所有資料 (位元組、MSMQ 訊息) 形成 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 訊息物件時啟動。 這個活動內的追蹤負責標頭處理作業。<br /><br /> 形成可分派的訊息後，便會在查詢對應的活動識別碼後切換至 ServiceHost ProcessAction 活動。|  
|D、S|處理動作 ‘[action]’。|ProcessAction|透過傳輸/安全性/RM 堆疊處理訊息，以便在接收時將訊息分派給使用者程式碼，傳送時則使用相反的順序來處理。<br /><br /> 在伺服器上，這個活動會使用傳播的活動識別碼如果傳送訊息標頭，以透過 「 活動傳播 」;否則，會建立新的 GUID。<br /><br /> 要求/回覆合約的回應訊息也會在該活動中處理。|  
|T|執行 ‘[IContract.Operation]’。|ExecuteUserCode|在服務端分派後執行使用者程式碼。 這個活動會提供界限，從使用者提供的程式碼描述 ServiceHost 程式碼。|  
  
## <a name="security-activities"></a>安全性活動  
 下表列出與安全性相關的所有活動。  
  
|活動名稱|活動類型|描述|  
|-------------------|-------------------|-----------------|  
|設定安全工作階段|SetupSecurity|只存在於用戶端。 包含所有的 RST*/SCT 交換，以驗證及設定安全性內容。 如果`propagateActivity` = `true`，此活動會與服務的對應處理動作 RST 合併\*/SCT 活動。|  
|關閉安全工作階段|SetupSecurity|存在於用戶端。 內含「取消」訊息交換，以關閉安全工作階段。 如果`propagateActivity` = `true`，此活動會與 「 取消 」 處理動作合併從服務。|  
  
 下表列出與 COM+ 相關的所有活動。  
  
|活動名稱|活動類型|描述|  
|-------------------|-------------------|-----------------|  
|建立 COM+ 執行個體|TransferToCOMPlus|1 個活動執行個體，用於 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 程式碼的每一個 COM+ 呼叫|  
|執行 COM +\<作業 >|TransferToCOMPlus|1 個活動執行個體，用於 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 程式碼的每一個 COM+ 呼叫|  
  
## <a name="wmi-activities"></a>WMI 活動  
 下表列出與 WMI 相關的所有活動。  
  
|活動名稱|活動類型|描述|  
|-------------------|-------------------|-----------------|  
|WMI get|WMIGetObject|使用者會從 WMI 擷取資料。|  
|WMI put|WmiPutInstance|使用者會以 WMI 更新資料。|
