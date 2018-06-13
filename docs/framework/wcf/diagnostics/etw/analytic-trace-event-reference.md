---
title: 分析的追蹤事件參考
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 0f8b4c15f2afefbc62b98dca66dcf3ccc31b1dc0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808633"
---
# <a name="analytic-trace-event-reference"></a>分析的追蹤事件參考
下表定義事件層級、 識別碼和與 WCF 分析追蹤關聯的訊息。  
  
## <a name="event-reference"></a>事件參考  
  
|事件 ID|事件層級|事件訊息|關鍵字|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|詳細資訊|集區正在配置 %1 位元組。|基礎結構|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|詳細資訊|BufferPool 的大小為 %1，由 %2 變更配額。|基礎結構|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|詳細資訊|IO 執行緒排程器回呼已叫用。|基礎結構|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|詳細資訊|IO 執行緒排程器回呼已叫用。|基礎結構|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|資訊|發送器在型別為 '%1' 的 ClientMessageInspector 上叫用了 'AfterReceiveReply'。|Troubleshooting，ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|資訊|發送器在型別 '%1' 的 ClientMessageInspector 上叫用了 'BeforeSendRequest'。|Troubleshooting，ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|資訊|發送器在 ClientParameterInspector 上叫用 'AfterCall'。 屬於類型 '%1'。|Troubleshooting，ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|資訊|發送器在型別 '%1' 的 ClientParameterInspector 上叫用了 'BeforeCall'。|Troubleshooting，ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|資訊|OperationInvoker 已叫用 '%1' 方法。|EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|資訊|發送器叫用了型別 '%1' (例外狀況型別為 '%3') 的 ErrorHandler。  ErrorHandled == '%2'。|Troubleshooting，ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|資訊|發送器已叫用型別為 '%1' 的 FaultProvider，其例外狀況型別為 '%2'。|Troubleshooting，ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|資訊|發送器在型別 '%1' 的 MessageInspector 上叫用了 'AfterReceiveReply'。|Troubleshooting，ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|資訊|發送器在型別 '%1' 的 MessageInspector 上叫用了 'BeforeSendRequest'。|Troubleshooting，ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|警告|已達到 '%1' 的節流閥限制 '%2'。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|資訊|發送器在型別 '%1' 的 ParameterInspector 上叫用 'AfterCall'。|Troubleshooting，ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|資訊|發送器在型別 '%1' 的 ParameterInspector 上叫用了 'BeforeCall'。|Troubleshooting，ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|ServiceHost 已啟動: '%1'。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|資訊|OperationInvoker 完成了對 '%1' 方法的呼叫。  此方法的呼叫持續時間為 '%2' 毫秒。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|資訊|傳輸收到來自 '%1' 的訊息。|Troubleshooting，ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|資訊|傳輸傳送了訊息至 '%1'。|Troubleshooting，ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|資訊|用戶端正在執行 '%2' 合約中定義的 '%1' 作業。 訊息將傳送至 '%3'。|Troubleshooting，ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|資訊|用戶端已完成執行 '%2' 合約中定義的 '%1' 作業。 訊息已傳送至 '%3'。|Troubleshooting，ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|錯誤|訊息處理期間發生了未處理的例外狀況 (型別為 '%2')。  完整例外狀況 ToString: %1。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|資訊|發送器已傳送訊息到傳輸。 相互關聯 ID == '%1'。|EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|資訊|發送器收到來自傳輸的訊息。 相互關聯 ID == '%1'。|EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|警告|由 OperationInvoker 叫用時，'%1' 方法擲回無法處理的例外。 此方法的呼叫持續時間為 '%2' 毫秒。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|警告|由 OperationInvoker 叫用時，'%1' 方法擲回 FaultException。 此方法的呼叫持續時間為 '%2' 毫秒。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|警告|'%2' 的 '%1' 節流閥限制為 70%。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|超出 %2 之啟用服務總數的 %1 閒置服務已關閉。|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|錯誤|名稱: '%1'，參考: '%2'，承載: %3。|UserEvents，HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|警告|名稱: '%1'，參考: '%2'，承載: %3。|UserEvents，HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|資訊|名稱: '%1'，參考: '%2'，承載: %3。|UserEvents，HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[401- StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|資訊|活動界限。|疑難排解|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|資訊|活動界限。|疑難排解|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|資訊|活動界限。|疑難排解|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|資訊|活動界限。|疑難排解|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|資訊|%1|Troubleshooting，WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|警告|%1|Troubleshooting，WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|已發出傳輸事件。|Troubleshooting，UserEvents，EndToEndMonitoring，ServiceModel，WFTracking，ServiceHost，WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|資訊|開始編譯。|WebHost|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|資訊|結束編譯。|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|資訊|ServiceHostFactory 開始建立。|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|資訊|ServiceHostFactory 結束建立。|WebHost|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|資訊|開始 CreateServiceHost。|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|資訊|結束 CreateServiceHost。|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|資訊|HostedTransportConfigurationManager 開始組態初始化。|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|資訊|HostedTransportConfigurationManager 結束組態初始化。|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|資訊|HostedTransportConfigurationManager 結束組態初始化。|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|資訊|ServiceHost 開啟已完成。|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|資訊|已從 AppDomain '%1' 接收虛擬路徑為 '%2' 的要求。|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|資訊|WebHostRequest 停止。|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|詳細資訊|已處理 ServiceActivation 元素相對位址：'%1'，標準化的相對位址 '%2'。||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|詳細資訊|傳入要求符合位址為 '%1' 的 ServiceActivation 元素。||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|詳細資訊|傳入要求符合 Asp.Net 路由中所定義且位址為 %1 的 WCF 服務。|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|詳細資訊|已加入具有 serviceType '%2' 和 serviceHostFactoryType '%3' 的新 Asp.Net 路由 '%1'。|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|詳細資訊|IncrementBusyCount 已呼叫。 來源︰%1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|詳細資訊|DecrementBusyCount 已呼叫。 來源︰%1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|詳細資訊|ServiceChannelOpen 已啟動。|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|資訊|ServiceChannelOpen 已完成。|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|資訊|ServiceChannelCall 已啟動。|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|資訊|ServiceChannel 非同步呼叫已啟動。|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|詳細資訊|HTTP 傳送要求開始。|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|詳細資訊|HTTP 傳送要求停止。|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|詳細資訊|從 HTTP 傳輸接收到的訊息。|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|資訊|訊息發送已啟動。|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|詳細資訊|啟動訊息發送的驗證。|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|詳細資訊|啟動訊息發送的授權。|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|資訊|訊息已發送完成。|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|資訊|ServiceChannel 開啟開始。|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|資訊|ServiceChannel 開啟停止。|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|資訊|HTTP 傳送資料流訊息已啟動。|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|錯誤|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|錯誤|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|錯誤|%1 連接集區索引鍵：%2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|資訊|%1 連接集區索引鍵：%2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|錯誤|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|錯誤|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|錯誤|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|資訊|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|錯誤|%1|配額|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|錯誤|%1|配額|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|資訊|%1|配額|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|資訊|%1|配額|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|錯誤|%1|配額|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|錯誤|%1|配額|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|詳細資訊|交涉權杖驗證器狀態快取比率：%1/%2|配額|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|詳細資訊|安全性工作階段比例：%1/%2|配額|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|詳細資訊|擱置連線比例：%1/%2|配額|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|詳細資訊|並行工作階段比例：%1/%2|配額|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|詳細資訊|並行工作階段比例：%1/%2|配額|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|詳細資訊|每個端點的傳出連線比例：%1/%2|配額|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|詳細資訊|每個端點的傳出連線比例：%1/%2|配額|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|詳細資訊|每個通道的擱置中訊息比例：%1/%2|配額|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|詳細資訊|並行的執行個體比例：%1/%2|配額|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|資訊|沒有擱置中訊息待接受|配額|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|警告|1%|配額|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|警告|在 ID 為 '%1' 之 MSMQ 訊息上已達接收重試計數|配額|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|錯誤|在 ID 為 '%1' 之 MSMQ 訊息上已超過最大重試循環|配額|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|詳細資訊|建立新的 '%1'|配額|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|詳細資訊|建立新的 '%1'|配額|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|錯誤|1%|配額|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|警告|無法完成 %1。|通道|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|警告|無法放棄 %1。|通道|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|警告|接收內容發生錯誤。|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|資訊|已放棄 %1，發生例外狀況 %2。|通道|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|資訊|快取通道處理站數目為：'%1'。  最多可以快取 '%2' 個通道處理站。|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|資訊|通道處理站已過時超出快取範圍，因為快取已達其 '%1' 的限制。|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|資訊|使用快取中找到的相符通道處理站。|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|資訊|無法從快取使用通道處理站，也就是停用快取執行個體。|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|資訊|使用 '%1' 的查詢複合是在要求 URI 上執行：'%2'。|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|錯誤|'%1' 作業發送有錯誤。|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|資訊|'%1' 作業成功發送。|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|資訊|編碼器讀取大小為 '%1' 位元組的訊息。|通道|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|資訊|編碼器寫入大小為 '%1' 位元組的訊息。|通道|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|錯誤|工作階段正在中止閒置的 URI 通道：'%1'。|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|詳細資訊|連接接受已啟動。|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|詳細資訊|ListenerId：%1 已接受 SocketId：%2。|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|詳細資訊|%1 的集區沒有可用的連線和 %2 忙碌的連線。|通道|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|詳細資訊|發送器已啟動還原序列化要求訊息。|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|詳細資訊|發送器已完成還原序列化要求訊息。|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|詳細資訊|發送器已啟動回覆訊息的序列化。|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|詳細資訊|發送器已完成回覆訊息的序列化。|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|詳細資訊|用戶端要求序列化已啟動。|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|詳細資訊|用戶端已完成要求訊息的序列化。|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|詳細資訊|用戶端已啟動還原序列化回覆訊息。|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|詳細資訊|用戶端已完成還原序列化回覆訊息。|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|詳細資訊|安全性交涉已啟動。|安全性|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|詳細資訊|安全性交涉已完成。|安全性|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|詳細資訊|SecurityTokenProvider 開啟已完成。|安全性|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|詳細資訊|外寄郵件受到保護。|安全性|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|詳細資訊|內送郵件已經過驗證。|安全性 ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|詳細資訊|服務執行個體擷取已啟動。|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|詳細資訊|已擷取服務執行個體。|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|詳細資訊|ChannelHandlerId：%1 - 訊息接收迴圈已啟動。|通道|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|詳細資訊|ChannelHandlerId：%1 - 訊息接收迴圈已停止。|通道|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|詳細資訊|已建立 ChannelFactory。|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|詳細資訊|管道連線接受已在 %1 上啟動。|通道|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|詳細資訊|管道連線已接受。|通道|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|詳細資訊|已啟動 %1 的連線建立。|通道|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|詳細資訊|已建立連線。|通道|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|詳細資訊|了解 '%1' 的工作階段前序編碼。|通道|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|錯誤|連線讀取器正在傳送錯誤 '%1'。|通道|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|詳細資訊|通訊端接受已關閉。|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Critical|服務主機發生錯誤。|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|詳細資訊|開啟 '%1' 的接聽項。|通道|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|詳細資訊|接聽項開啟完成。|通道|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|詳細資訊|達到伺服器最大的共用連線配額。|配額|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|錯誤|遠端位址 %2 的 SocketId：%1 逾時。|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|警告|遠端位址 %2 的 SocketId：%1 發生連線重設錯誤。|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|詳細資訊|服務安全性交涉已完成。|安全性|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|錯誤|安全性交涉處理失敗。|安全性|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|詳細資訊|安全性驗證成功。|安全性|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|錯誤|安全性驗證失敗。|安全性|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|詳細資訊|%1 的通訊端重複。|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|詳細資訊|安全性模擬成功。|安全性|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|警告|安全性模擬失敗。|安全性|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|警告|HTTP 通道要求中止。|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|警告|HTTP 通道回應中止。|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|警告|HTTP 驗證失敗。|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|詳細資訊|已啟動 URI '%1' 的 SharedListenerProxy 登錄。|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|詳細資訊|SharedListenerProxy 登錄停止。|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|錯誤|SharedListenerProxy 登錄失敗，狀態為 '%1'。|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|錯誤|ConnectionPoolPreambleFailed。|通道|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|詳細資訊|SslOnAcceptUpgradeStart|安全性|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|詳細資訊|SslOnAcceptUpgradeStop|安全性|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|詳細資訊|BinaryMessageEncoder 開始編碼訊息。|通道|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|詳細資訊|MtomMessageEncoder 開始編碼訊息。|通道|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|詳細資訊|TextMessageEncoder 開始編碼訊息。|通道|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|詳細資訊|BinaryMessageEncoder 開始解碼訊息。|通道|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|詳細資訊|MtomMessageEncoder 開始解碼訊息。|通道|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|詳細資訊|TextMessageEncoder 開始解碼訊息。|通道|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|資訊|HTTP 傳輸開始接收訊息。|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|詳細資訊|SocketId：%1 已讀取從 '%3' 讀取的 '%2' 個位元組。|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|詳細資訊|SocketId：%1 已讀取從 '%3' 讀取的 '%2' 個位元組。|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|詳細資訊|SocketId：%1 將 '%2' 個位元組寫入 '%3'。|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|詳細資訊|SocketId：%1 將 '%2' 個位元組寫入 '%3'。|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|詳細資訊|SessionId：%1 認可已傳送。|通道|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|資訊|SessionId：%1 重新連線中。|通道|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|資訊|SessionId：%1 發生錯誤。|通道|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|詳細資訊|WindowsStreamSecurity 正在初始化安全性升級。|安全性|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|詳細資訊|Windows 接受升級的資料流安全性。|安全性|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|警告|SocketId：%1 正在中止。|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|詳細資訊|HttpGetContext 開始。|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|詳細資訊|用戶端傳送前序編碼開始。|通道|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|詳細資訊|用戶端傳送前序編碼停止。|通道|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|警告|HTTP 訊息接收失敗。|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|資訊|TransactionScope 是以 LocalIdentifier：'%1' 和 DistributedIdentifier：'%2' 建立的。|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|資訊|資料流訊息由編碼器讀取。|通道|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|資訊|資料流訊息由編碼器寫入。|通道|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|資訊|編碼器將訊息寫入為非同步。|通道|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|資訊|BufferId：%1 已完成寫入 '%2' 個位元組至基礎資料流。|通道|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|資訊|編碼器將訊息寫入為非同步。|通道|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|詳細資訊|管線共用記憶體建立在 '%1'。|通道|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|詳細資訊|NamedPipe '%1' 已建立。|通道|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|詳細資訊|簽章驗證已啟動。|安全性|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|詳細資訊|簽章驗證成功。|安全性|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|詳細資訊|已開始解密包裝的金鑰。|安全性|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|詳細資訊|已成功解密包裝的金鑰。|安全性|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|詳細資訊|已開始處理加密的資料。|安全性|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|詳細資訊|已成功處理加密的資料。|安全性|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|詳細資訊|Http 訊息處理常式已開始處理輸入要求。|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|詳細資訊|Http 訊息處理常式已開始以非同步方式處理輸入要求。|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|詳細資訊|Http 訊息處理常式已完成輸入要求的處理。|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|警告|Http 訊息處理常式發生錯誤。|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|錯誤|WebSocket 連接逾時。|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|詳細資訊|Http 訊息處理常式已開始處理回應。|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|詳細資訊|Http 訊息處理常式已開始以非同步方式處理回應。|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|詳細資訊|Http 訊息處理常式已完成回應的處理。|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|詳細資訊|WebSocket 連接要求 '%1' 開始傳送。|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|詳細資訊|WebSocketId：%1 已傳送連接要求。|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|詳細資訊|WebSocket 開始接受連接。|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|詳細資訊|WebSocketId：%1 已接受連接。|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|錯誤|WebSocket 連接遭拒，狀態碼為 '%1'|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|錯誤|WebSocket 連接要求失敗：'%1'|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|錯誤|WebSocketId：%1 連接已中止。|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|詳細資訊|WebSocketId：%1 將 '%2' 個位元組寫入 '%3'。|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|詳細資訊|WebSocketId：%1 非同步寫入停止。|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|詳細資訊|WebSocketId：%1 開始讀取。|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|詳細資訊|WebSocketId：%1 從 '%3' 中讀取 '%2' 個位元組。|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|詳細資訊|WebSocketId：%1 將關閉訊息傳送至具有關閉狀態 '%3' 的 '%2'。|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|詳細資訊|WebSocketId：%1 將關閉輸出訊息傳送至具有關閉狀態 '%3' 的 '%2'。|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|詳細資訊|WebSocketId：%1 已關閉連接。|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|詳細資訊|WebSocketId：%1 收到具有狀態 '%2' 的連接關閉訊息。|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|詳細資訊|正在使用來自型別為 '%1' 的用戶端 WebSocket 工廠的 WebSocketVersion。|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|詳細資訊|正在建立工廠型別 '%1' 的用戶端 WebSocket。|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|資訊|XamlServicesLoad 開始|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|資訊|XamlServicesLoad 停止|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|資訊|CreateWorkflowServiceHost 開始|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|資訊|CreateWorkflowServiceHost 停止|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|資訊|服務啟用開始|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|資訊|服務啟用停止|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|詳細資訊|可用的記憶體 (位元組)：%1|配額|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|資訊|路由服務正在關閉用戶端 '%1'。|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|警告|路由服務用戶端 '%1' 發生錯誤。|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|資訊|路由服務單向訊息即將完成。|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|錯誤|處理位址 '%1' 的端點上的訊息時，路由服務失敗。|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|資訊|路由服務正在為下列端點建立用戶端：'%1'。|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|詳細資訊|路由服務已設定 RouteOnHeadersOnly：%1，SoapProcessingEnabled：%2，EnsureOrderedDispatch：%3。|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|資訊|路由服務要求回覆訊息即將完成。|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|詳細資訊|路由服務將 ID：'%1' 的訊息傳送到 %2 端點清單。|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|資訊|已對路由服務套用新的 RoutingConfiguration。|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|資訊|路由服務正在處理訊息，ID：'%1'，動作：'%2'，輸入 URL：'%3'，接收於交易：%4。|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|資訊|路由服務正在將 ID 為：'%1' [作業%2] 的訊息傳輸至 '%3'。|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|資訊|路由服務正在認可下列 ID 的交易：'%1'。|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|錯誤|路由服務元件 %1 遇到雙工回呼例外狀況。|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|資訊|ID：'%1' 的路由服務訊息 [作業 %2] 已移到備份端點 '%3'。|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|資訊|路由服務為處理訊息，已建立 ID 為 '%1' 的新交易。|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|警告|關閉傳出用戶端 '%1' 時路由服務失敗。|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|資訊|路由服務正在傳回動作為 '%1' 的回應訊息。|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|警告|路由服務正在傳回動作為 '%1' 的錯誤回應訊息。|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|詳細資訊|路由服務正在為 ID：'%1' 的訊息呼叫 ReceiveContext.Complete。|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|警告|路由服務正在為 ID 為 '%1' 的訊息呼叫 ReceiveContext.Abandon。|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|詳細資訊|路由服務會使用現有的交易 '%1' 傳送訊息。|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|警告|傳送至 '%1' 時，路由服務失敗。|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|資訊|路由服務 MessageFilterTable 比對開始。|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|資訊|路由服務 MessageFilterTable 比對停止。|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|詳細資訊|路由服務正在通道：'%1' 上呼叫中止。|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|詳細資訊|路由服務已經處理過例外狀況。|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|資訊|路由服務成功地將 ID：'%1 的訊息 [作業 %2] 傳輸至 '%3'。|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|詳細資訊|透過 '%1' 與傳輸接聽項工作階段一起接收|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Critical|FailFastException。|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|錯誤|服務啟動管道時發生錯誤。|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|詳細資訊|工作階段分派已啟動。|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|警告|'%1' 的工作階段分派失敗，因為擱置中的工作階段佇列已填滿 '%2' 擱置中的項目。|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|詳細資訊|訊息佇列登錄開始。|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|錯誤|URI：'%2' 的訊息佇列登錄已中止，狀態為：'%1'。|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|詳細資訊|為 URI：'%1' 解除登錄訊息佇列成功。|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|錯誤|URI：'%1' 的訊息佇列登錄失敗，狀態為：'%2'。|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|資訊|URI '%1' 的訊息佇列登錄已完成。|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|錯誤|訊息佇列無法複製通訊端。|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|詳細資訊|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|詳細資訊|開始在 URI：'%1' 上接聽 Tcp 傳輸接聽項。|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|詳細資訊|TCP 傳輸接聽項正在接聽。|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|錯誤|錯誤碼：%1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|資訊|已關閉所有完成的接聽項通道執行個體。|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|錯誤|錯誤碼：%1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|錯誤|錯誤碼：%1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|詳細資訊|WAS 已連線。|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|詳細資訊|WAS 已中斷連線。|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|詳細資訊|uri：%1 上的管線傳輸接聽項接聽開始。|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|詳細資訊|管道傳輸接聽項接聽停止。|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|資訊|工作階段分派成功。|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|錯誤|工作階段分派失敗。|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Critical|WAS 連線逾時。|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|詳細資訊|路由表查閱已啟動。|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|詳細資訊|路由表查閱已完成。|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|詳細資訊|擱置中的工作階段佇列比例：%1/%2|配額|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|警告|無法記錄訊息，因為它已超過 ETW 事件大小|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|警告|在 DiscoveryClientChannel 中建立的 DiscoveryClient 無法關閉，因此已經中止。|探索|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|資訊|ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的。 這可能是因為 DiscoveryService 仍在嘗試傳送回應給 DiscoveryClient。|探索|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|資訊|DiscoveryClient 收到來自 DiscoveryProxy 的多點傳送隱藏訊息。|探索|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|資訊|messageId='%2' 的 %1 訊息已由 DiscoveryClient 丟棄，因為對應的 %3 作業已完成。|探索|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|警告|一項 messageId='%2' 的 %1 訊息已遭丟棄，因為它的內容無效。|探索|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|警告|messageId='%2' 且 relatesTo='%3' 的 %1 訊息已由 DiscoveryClient 丟棄，因為對應的 %4 作業已完成，或是 relatesTo 值無效。|探索|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|警告|messageId='%1' 的探索要求訊息已遭丟棄，因為它的 ReplyTo 地址無效。|探索|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|警告|%1 訊息已遭丟棄，因為它沒有任何內容。|探索|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|警告|%1 訊息已遭丟棄，因為訊息標頭未包含必要的 MessageId 屬性。|探索|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|警告|messageId='%2' 的 %1 訊息已遭 DiscoveryClient 丟棄，因為它沒有 DiscoveryMessageSequence 屬性。|探索|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|警告|messageId='%2' 的 %1 訊息已遭 DiscoveryClient 丟棄，因為訊息標頭未包含必要的 RelatesTo 屬性。|探索|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|警告|messageId='%1' 的探索要求訊息已遭丟棄，因為它沒有 ReplyTo 地址。|探索|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|警告|messageId='%2' 的 %1 訊息已遭丟棄，因為它是重複項目。|探索|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|資訊|EndpointAddress='%1' 且 ListenUri='%2' 的端點可搜尋性已遭停用。|探索|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|資訊|EndpointAddress='%1' 且 ListenUri='%2' 的端點可搜尋性已經啟用。|探索|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|詳細資訊|DiscoveryClientChannel 中已初始化尋找作業以探索端點。|探索|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|警告|DiscoveryClientChannel 無法以 EndpointAddress='%1' 且 Via='%2' 的探索結果端點建立通道。 DiscoveryClientChannel 現在將嘗試使用下一個可用的探索結果端點。|探索|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|警告|DiscoveryClientChannel 無法以 EndpointAddress='%1' 且 Via='%2' 的探索結果端點開啟通道。 DiscoveryClientChannel 現在將嘗試使用下一個可用的探索結果端點。|探索|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|資訊|DiscoveryClientChannel 成功發現一個端點並使用它開啟通道。 用戶端已使用 EndpointAddress='%1' 和 Via='%2' 連接至服務。|探索|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|資訊|SynchronizationContext 已由 DiscoveryClientChannel 重設為其原始值 %1。|探索|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|資訊|在初始化尋找作業之前，SynchronizationContext 已由 DiscoveryClientChannel 設定為 null。|探索|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|詳細資訊|DataContract 使用代理序列化 %1 開始。|序列化|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|詳細資訊|DataContract 使用代理序列化停止。|序列化|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|詳細資訊|DataContract 使用代理還原序列化 %1 開始。|序列化|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|詳細資訊|DataContract 使用代理還原序列化停止。|序列化|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|詳細資訊|ImportKnownTypes 開始。|序列化|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|詳細資訊|ImportKnownTypes 停止。|序列化|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|詳細資訊|解析 %1 的 DataContract 解析程式開始。|序列化|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|詳細資訊|DataContract 產生 %2 的 %1 寫入器開始。|序列化|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|詳細資訊|DataContract 產生寫入器停止。|序列化|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|詳細資訊|DataContract 產生 %2 的 %1 讀取器開始。|序列化|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|詳細資訊|DataContract 產生停止。|序列化|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|詳細資訊|Json 產生 %2 的 %1 讀取器開始。|序列化|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|詳細資訊|Json 讀取器產生停止。|序列化|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|詳細資訊|Json 產生 %2 的 %1 寫入器開始。|序列化|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|詳細資訊|Json 產生寫入器停止。|序列化|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|詳細資訊|'%1' 的產生 Xml 可序列化開始。|序列化|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|詳細資訊|產生 Xml 可序列化停止。|序列化|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|詳細資訊|JsonMessageEncoder 開始解碼訊息。|通道|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|詳細資訊|JsonMessageEncoder 開始編碼訊息。|通道|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|詳細資訊|SecurityToken (類型 '%1' 和 ID '%2') 驗證已開始。|安全性|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|詳細資訊|SecurityToken (類型 '%1' 和 ID '%2') 驗證成功。|安全性|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|錯誤|SecurityToken (類型 '%1' 和 ID '%2') 驗證失敗。 %3|安全性|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|詳細資訊|擷取 tokenId：%2 中的簽發者名稱：%1 成功。|安全性|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|錯誤|擷取 tokenId：%1 中的簽發者名稱失敗。|安全性|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|詳細資訊|已開始處理同盟訊息。|安全性|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|詳細資訊|已成功處理同盟訊息。|安全性|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|詳細資訊|正在從啟動的表單張貼建立同盟訊息。|安全性|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|詳細資訊|已成功從表單張貼建立同盟訊息。|安全性|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|詳細資訊|已開始從工作階段 Cookie 讀取工作階段權杖。|安全性|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|詳細資訊|已成功從工作階段 Cookie 讀取工作階段權杖。|安全性|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|詳細資訊|已開始從工作階段權杖設定主體。|安全性|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|詳細資訊|已成功從工作階段權杖設定主體。|安全性|  
|[57393 - AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|資訊|AppDomain 卸載。 AppDomain.FriendlyName %1、ProcessName %2、ProcessId %3。|基礎結構|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|資訊|正在處理例外狀況。|基礎結構|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|錯誤|發生未預期的失敗。 應用程式不應該嘗試處理此錯誤。 為方便診斷，這個英文訊息與下列失敗相關：%1。|基礎結構|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|警告|正在擲回例外狀況。 來源 %1。|基礎結構|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Critical|未處理的例外狀況。|基礎結構|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Critical|已寫入 EventLog。|基礎結構|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|錯誤|已寫入 EventLog。|基礎結構|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|資訊|已寫入 EventLog。|基礎結構|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|詳細資訊|已寫入 EventLog。|基礎結構|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|警告|已寫入 EventLog。|基礎結構|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|警告|正在處理例外狀況。|基礎結構|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|資訊|URL '%1' 裝載了具有根元素型別 '%2' 的 XAML 文件。 系統挑選 HTTP 處理常式型別 '%3' 來服務對這個 URL 提出的所有要求。|WebHost|
