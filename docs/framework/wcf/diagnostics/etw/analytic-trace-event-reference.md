---
title: 分析的追蹤事件參考
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 1b44e6b0abf0fc48b43ae17cbd24780e46ae518d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798121"
---
# <a name="analytic-trace-event-reference"></a>分析的追蹤事件參考
下表定義與 WCF 分析追蹤相關聯的事件層級、識別碼和訊息。  
  
## <a name="event-reference"></a>事件參考  
  
|事件 ID|事件層級|事件訊息|關鍵字|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](131-bufferpoolallocation.md)|詳細資訊|集區正在配置 %1 位元組。|基礎結構|  
|[132 - BufferPoolChangeQuota](132-bufferpoolchangequota.md)|詳細資訊|BufferPool 的大小為 %1，由 %2 變更配額。|基礎結構|  
|[133 - ActionItemScheduled](133-actionitemscheduled.md)|詳細資訊|IO 執行緒排程器回呼已叫用。|基礎結構|  
|[134 - ActionItemCallbackInvoked](134-actionitemcallbackinvoked.md)|詳細資訊|IO 執行緒排程器回呼已叫用。|基礎結構|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](201-clientmessageinspectorafterreceiveinvoked.md)|內容|發送器在型別為 '%1' 的 ClientMessageInspector 上叫用了 'AfterReceiveReply'。|Troubleshooting，ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](202-clientmessageinspectorbeforesendinvoked.md)|內容|發送器在型別 '%1' 的 ClientMessageInspector 上叫用了 'BeforeSendRequest'。|Troubleshooting，ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](203-clientparameterinspectoraftercallinvoked.md)|內容|發送器在 ClientParameterInspector 上叫用 'AfterCall'。 屬於類型 '%1'。|Troubleshooting，ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](204-clientparameterinspectorbeforecallinvoked.md)|內容|發送器在型別 '%1' 的 ClientParameterInspector 上叫用了 'BeforeCall'。|Troubleshooting，ServiceModel|  
|[205 - OperationInvoked](205-operationinvoked.md)|內容|OperationInvoker 已叫用 '%1' 方法。|EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[206 - ErrorHandlerInvoked](206-errorhandlerinvoked.md)|內容|發送器叫用了型別 '%1' (例外狀況型別為 '%3') 的 ErrorHandler。  ErrorHandled == '%2'。|Troubleshooting，ServiceModel|  
|[207 - FaultProviderInvoked](207-faultproviderinvoked.md)|內容|發送器已叫用型別為 '%1' 的 FaultProvider，其例外狀況型別為 '%2'。|Troubleshooting，ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](208-messageinspectorafterreceiveinvoked.md)|內容|發送器在型別 '%1' 的 MessageInspector 上叫用了 'AfterReceiveReply'。|Troubleshooting，ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](209-messageinspectorbeforesendinvoked.md)|內容|發送器在型別 '%1' 的 MessageInspector 上叫用了 'BeforeSendRequest'。|Troubleshooting，ServiceModel|  
|[210 - MessageThrottleExceeded](210-messagethrottleexceeded.md)|警告|已達到 '%1' 的節流閥限制 '%2'。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](211-parameterinspectoraftercallinvoked.md)|內容|發送器在型別 '%1' 的 ParameterInspector 上叫用 'AfterCall'。|Troubleshooting，ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](212-parameterinspectorbeforecallinvoked.md)|內容|發送器在型別 '%1' 的 ParameterInspector 上叫用了 'BeforeCall'。|Troubleshooting，ServiceModel|  
|[213 - ServiceHostStarted](213-servicehoststarted.md)|LogAlways|ServiceHost 已啟動: '%1'。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[214 - OperationCompleted](214-operationcompleted.md)|內容|OperationInvoker 完成了對 '%1' 方法的呼叫。  此方法的呼叫持續時間為 '%2' 毫秒。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[215 - MessageReceivedByTransport](215-messagereceivedbytransport.md)|內容|傳輸收到來自 '%1' 的訊息。|Troubleshooting，ServiceModel|  
|[216 - MessageSentByTransport](216-messagesentbytransport.md)|內容|傳輸傳送了訊息至 '%1'。|Troubleshooting，ServiceModel|  
|[217 - ClientOperationPrepared](217-clientoperationprepared.md)|內容|用戶端正在執行 '%2' 合約中定義的 '%1' 作業。 訊息將傳送至 '%3'。|Troubleshooting，ServiceModel|  
|[218 - ClientOperationCompleted](218-clientoperationcompleted.md)|內容|用戶端已完成執行 '%2' 合約中定義的 '%1' 作業。 訊息已傳送至 '%3'。|Troubleshooting，ServiceModel|  
|[219 - ServiceException](219-serviceexception.md)|Error|訊息處理期間發生了未處理的例外狀況 (型別為 '%2')。  完整例外狀況 ToString: %1。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[220 - MessageSentToTransport](220-messagesenttotransport.md)|內容|發送器已傳送訊息到傳輸。 相互關聯 ID == '%1'。|EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[221 - MessageReceivedFromTransport](221-messagereceivedfromtransport.md)|內容|發送器收到來自傳輸的訊息。 相互關聯 ID == '%1'。|EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[222 - OperationFailed](222-operationfailed.md)|警告|由 OperationInvoker 叫用時，'%1' 方法擲回無法處理的例外。 此方法的呼叫持續時間為 '%2' 毫秒。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[223 - OperationFaulted](223-operationfaulted.md)|警告|由 OperationInvoker 叫用時，'%1' 方法擲回 FaultException。 此方法的呼叫持續時間為 '%2' 毫秒。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](224-messagethrottleatseventypercent.md)|警告|'%2' 的 '%1' 節流閥限制為 70%。|HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[226 - IdleServicesClosed](226-idleservicesclosed.md)|LogAlways|超出 %2 之啟用服務總數的 %1 閒置服務已關閉。|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](301-userdefinederroroccurred.md)|Error|名稱: '%1'，參考: '%2'，承載: %3。|UserEvents，HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[302 - UserDefinedWarningOccurred](302-userdefinedwarningoccurred.md)|警告|名稱: '%1'，參考: '%2'，承載: %3。|UserEvents，HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[303 - UserDefinedInformationEventOccured](303-userdefinedinformationeventoccured.md)|內容|名稱: '%1'，參考: '%2'，承載: %3。|UserEvents，HealthMonitoring，EndToEndMonitoring，Troubleshooting，ServiceModel|  
|[401- StopSignPostEvent](401-stopsignpostevent.md)|內容|活動界限。|疑難排解|  
|[402 - StartSignpostEvent](402-startsignpostevent.md)|內容|活動界限。|疑難排解|  
|[403 - SuspendSignpostEvent](403-suspendsignpostevent.md)|內容|活動界限。|疑難排解|  
|[404 - ResumeSignpostEvent](404-resumesignpostevent.md)|內容|活動界限。|疑難排解|  
|[451 - MessageLogInfo](451-messageloginfo.md)|內容|%1|Troubleshooting，WCFMessageLogging|  
|[452 - MessageLogWarning](452-messagelogwarning.md)|警告|%1|Troubleshooting，WCFMessageLogging|  
|[499 - TransferEmitted](499-transferemitted.md)|LogAlways|已發出傳輸事件。|Troubleshooting，UserEvents，EndToEndMonitoring，ServiceModel，WFTracking，ServiceHost，WCFMessageLogging|  
|[501 - CompilationStart](501-compilationstart.md)|內容|開始編譯。|WebHost|  
|[502 - CompilationStop](502-compilationstop.md)|內容|結束編譯。|WebHost|  
|[503 - ServiceHostFactoryCreationStart](503-servicehostfactorycreationstart.md)|內容|ServiceHostFactory 開始建立。|WebHost|  
|[504 - ServiceHostFactoryCreationStop](504-servicehostfactorycreationstop.md)|內容|ServiceHostFactory 結束建立。|WebHost|  
|[505 - CreateServiceHostStart](505-createservicehoststart.md)|內容|開始 CreateServiceHost。|WebHost|  
|[506 - CreateServiceHostStop](506-createservicehoststop.md)|內容|結束 CreateServiceHost。|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](507-hostedtransportconfigurationmanagerconfiginitstart.md)|內容|HostedTransportConfigurationManager 開始組態初始化。|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](508-hostedtransportconfigurationmanagerconfiginitstop.md)|內容|HostedTransportConfigurationManager 結束組態初始化。|WebHost|  
|[509 - ServiceHostOpenStart](509-servicehostopenstart.md)|內容|HostedTransportConfigurationManager 結束組態初始化。|ServiceHost|  
|[510 - ServiceHostOpenStop](510-servicehostopenstop.md)|內容|ServiceHost 開啟已完成。|ServiceHost|  
|[513 - WebHostRequestStart](513-webhostrequeststart.md)|內容|已從 AppDomain '%1' 接收虛擬路徑為 '%2' 的要求。|WebHost|  
|[514 - WebHostRequestStop](514-webhostrequeststop.md)|內容|WebHostRequest 停止。|WebHost|  
|[601 - CBAEntryRead](601-cbaentryread.md)|詳細資訊|已處理 ServiceActivation 元素相對位址：'%1'，標準化的相對位址 '%2'。||  
|[602 - CBAMatchFound](602-cbamatchfound.md)|詳細資訊|傳入要求符合位址為 '%1' 的 ServiceActivation 元素。||  
|[603 - AspNetRoutingService](603-aspnetroutingservice.md)|詳細資訊|傳入要求符合 Asp.Net 路由中所定義且位址為 %1 的 WCF 服務。|RoutingServices|  
|[604 - AspNetRoute](604-aspnetroute.md)|詳細資訊|已加入具有 serviceType '%2' 和 serviceHostFactoryType '%3' 的新 Asp.Net 路由 '%1'。|RoutingServices|  
|[605 - IncrementBusyCount](605-incrementbusycount.md)|詳細資訊|IncrementBusyCount 已呼叫。 來源︰%1|WebHost|  
|[606 - DecrementBusyCount](606-decrementbusycount.md)|詳細資訊|DecrementBusyCount 已呼叫。 來源︰%1|WebHost|  
|[701 - ServiceChannelOpenStart](701-servicechannelopenstart.md)|詳細資訊|ServiceChannelOpen 已啟動。|WebHost|  
|[702 - ServiceChannelOpenStop](702-servicechannelopenstop.md)|內容|ServiceChannelOpen 已完成。|ServiceModel|  
|[703 - ServiceChannelCallStart](703-servicechannelcallstart.md)|內容|ServiceChannelCall 已啟動。|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](704-servicechannelbegincallstart.md)|內容|ServiceChannel 非同步呼叫已啟動。|ServiceModel|  
|[706 - HttpSendMessageStart](706-httpsendmessagestart.md)|詳細資訊|HTTP 傳送要求開始。|HTTP|  
|[707 - HttpSendStop](707-httpsendstop.md)|詳細資訊|HTTP 傳送要求停止。|HTTP|  
|[708 - HttpMessageReceiveStart](708-httpmessagereceivestart.md)|詳細資訊|從 HTTP 傳輸接收到的訊息。|HTTP|  
|[709 - DispatchMessageStart](709-dispatchmessagestart.md)|內容|訊息發送已啟動。|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](710-httpcontextbeforeprocessauthentication.md)|詳細資訊|啟動訊息發送的驗證。|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](711-dispatchmessagebeforeauthorization.md)|詳細資訊|啟動訊息發送的授權。|ServiceModel|  
|[712 - DispatchMessageStop](712-dispatchmessagestop.md)|內容|訊息已發送完成。|ServiceModel|  
|[715 - ClientChannelOpenStart](715-clientchannelopenstart.md)|內容|ServiceChannel 開啟開始。|ServiceModel|  
|[716 - ClientChannelOpenStop](716-clientchannelopenstop.md)|內容|ServiceChannel 開啟停止。|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](717-httpsendstreamedmessagestart.md)|內容|HTTP 傳送資料流訊息已啟動。|HTTP|  
|[1400 - ChannelInitializationTimeout](1400-channelinitializationtimeout.md)|Error|1%|ServiceModel|  
|[1401 - CloseTimeout](1401-closetimeout.md)|Error|1%|ServiceModel|  
|[1402 - IdleTimeout](1402-idletimeout.md)|Error|%1 連接集區索引鍵：%2|ServiceModel|  
|[1403 - LeaseTimeout](1403-leasetimeout.md)|內容|%1 連接集區索引鍵：%2|ServiceModel|  
|[1405 - OpenTimeout](1405-opentimeout.md)|Error|%1|ServiceModel|  
|[1406 - ReceiveTimeout](1406-receivetimeout.md)|Error|%1|ServiceModel|  
|[1407 - SendTimeout](1407-sendtimeout.md)|Error|%1|ServiceModel|  
|[1409 - InactivityTimeout](1409-inactivitytimeout.md)|內容|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](1416-maxreceivedmessagesizeexceeded.md)|Error|%1|配額|  
|[1417 - MaxSentMessageSizeExceeded](1417-maxsentmessagesizeexceeded.md)|Error|%1|配額|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](1418-maxoutboundconnectionsperendpointexceeded.md)|內容|%1|配額|  
|[1419 - MaxPendingConnectionsExceeded](1419-maxpendingconnectionsexceeded.md)|內容|%1|配額|  
|[1420 - ReaderQuotaExceeded](1420-readerquotaexceeded.md)|Error|%1|配額|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Error|%1|配額|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](1423-negotiatetokenauthenticatorstatecacheratio.md)|詳細資訊|交涉權杖驗證器狀態快取比率：%1/%2|配額|  
|[1424 - SecuritySessionRatio](1424-securitysessionratio.md)|詳細資訊|安全性工作階段比例：%1/%2|配額|  
|[1430 - PendingConnectionsRatio](1430-pendingconnectionsratio.md)|詳細資訊|擱置連線比例：%1/%2|配額|  
|[1431 - ConcurrentCallsRatio](1431-concurrentcallsratio.md)|詳細資訊|並行工作階段比例：%1/%2|配額|  
|[1432 - ConcurrentSessionsRatio](1432-concurrentsessionsratio.md)|詳細資訊|並行工作階段比例：%1/%2|配額|  
|[1433 - OutboundConnectionsPerEndpointRatio](1433-outboundconnectionsperendpointratio.md)|詳細資訊|每個端點的傳出連線比例：%1/%2|配額|  
|[1436 - PendingMessagesPerChannelRatio](1436-pendingmessagesperchannelratio.md)|詳細資訊|每個通道的擱置中訊息比例：%1/%2|配額|  
|[1438 - ConcurrentInstancesRatio](1438-concurrentinstancesratio.md)|詳細資訊|並行的執行個體比例：%1/%2|配額|  
|[1439 - PendingAcceptsAtZero](1439-pendingacceptsatzero.md)|內容|沒有擱置中訊息待接受|配額|  
|[1441 - MaxSessionSizeReached](1441-maxsessionsizereached.md)|警告|1%|配額|  
|[1442 - ReceiveRetryCountReached](1442-receiveretrycountreached.md)|警告|在 ID 為 '%1' 之 MSMQ 訊息上已達接收重試計數|配額|  
|[1443 - MaxRetryCyclesExceededMsmq](1443-maxretrycyclesexceededmsmq.md)|Error|在 ID 為 '%1' 之 MSMQ 訊息上已超過最大重試循環|配額|  
|[1445 - ReadPoolMiss](1445-readpoolmiss.md)|詳細資訊|建立新的 '%1'|配額|  
|[1446 - WritePoolMiss](1446-writepoolmiss.md)|詳細資訊|建立新的 '%1'|配額|  
|[1451 - MaxRetryCyclesExceeded](1451-maxretrycyclesexceeded.md)|Error|1%|配額|  
|[3300 - ReceiveContextCompleteFailed](3300-receivecontextcompletefailed.md)|警告|無法完成 %1。|通道|  
|[3301 - ReceiveContextAbandonFailed](3301-receivecontextabandonfailed.md)|警告|無法放棄 %1。|通道|  
|[3303 - ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|警告|接收內容發生錯誤。|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|內容|已放棄 %1，發生例外狀況 %2。|通道|  
|[3305 - ClientBaseCachedChannelFactoryCount](3305-clientbasecachedchannelfactorycount.md)|內容|快取通道處理站數目為：'%1'。  最多可以快取 '%2' 個通道處理站。|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](3306-clientbasechannelfactoryagedoutofcache.md)|內容|通道處理站已過時超出快取範圍，因為快取已達其 '%1' 的限制。|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](3307-clientbasechannelfactorycachehit.md)|內容|使用快取中找到的相符通道處理站。|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](3308-clientbaseusinglocalchannelfactory.md)|內容|未從快取使用通道處理站，亦即已停用實例的快取。|ServiceModel|  
|[3309 - QueryCompositionExecuted](3309-querycompositionexecuted.md)|內容|使用 '%1' 的查詢複合是在要求 URI 上執行：'%2'。|ServiceModel|  
|[3310 - DispatchFailed](3310-dispatchfailed.md)|Error|'%1' 作業發送有錯誤。|ServiceModel|  
|[3311 - DispatchSuccessful](3311-dispatchsuccessful.md)|內容|'%1' 作業成功發送。|ServiceModel|  
|[3312 - MessageReadByEncoder](3312-messagereadbyencoder.md)|內容|編碼器讀取大小為 '%1' 位元組的訊息。|通道|  
|[3312 - MessageReadByEncoder](3312-messagereadbyencoder.md)|內容|編碼器寫入大小為 '%1' 位元組的訊息。|通道|  
|[3314 - SessionIdleTimeout](3314-sessionidletimeout.md)|Error|工作階段正在中止閒置的 URI 通道：'%1'。|ServiceModel|  
|[3319 - SocketAcceptEnqueued](3319-socketacceptenqueued.md)|詳細資訊|連接接受已啟動。|TCP|  
|[3320 - SocketAccepted](3320-socketaccepted.md)|詳細資訊|ListenerId：%1 已接受 SocketId：%2。|TCP|  
|[3321 - ConnectionPoolMiss](3321-connectionpoolmiss.md)|詳細資訊|%1 的集區沒有可用的連線和 %2 忙碌的連線。|通道|  
|[3322 - DispatchFormatterDeserializeRequestStart](3322-dispatchformatterdeserializerequeststart.md)|詳細資訊|發送器已啟動還原序列化要求訊息。|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](3323-dispatchformatterdeserializerequeststop.md)|詳細資訊|發送器已完成還原序列化要求訊息。|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](3324-dispatchformatterserializereplystart.md)|詳細資訊|發送器已啟動回覆訊息的序列化。|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](3325-dispatchformatterserializereplystop.md)|詳細資訊|發送器已完成回覆訊息的序列化。|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](3326-clientformatterserializerequeststart.md)|詳細資訊|用戶端要求序列化已啟動。|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](3327-clientformatterserializerequeststop.md)|詳細資訊|用戶端已完成要求訊息的序列化。|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](3328-clientformatterdeserializereplystart.md)|詳細資訊|用戶端已啟動還原序列化回覆訊息。|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](3329-clientformatterdeserializereplystop.md)|詳細資訊|用戶端已完成還原序列化回覆訊息。|ServiceModel|  
|[3330 - SecurityNegotiationStart](3330-securitynegotiationstart.md)|詳細資訊|安全性交涉已啟動。|安全性|  
|[3331 - SecurityNegotiationStop](3331-securitynegotiationstop.md)|詳細資訊|安全性交涉已完成。|安全性|  
|[3332 - SecurityTokenProviderOpened](3332-securitytokenprovideropened.md)|詳細資訊|SecurityTokenProvider 開啟已完成。|安全性|  
|[3333 - OutgoingMessageSecured](3333-outgoingmessagesecured.md)|詳細資訊|外寄郵件受到保護。|安全性|  
|[3334 - IncomingMessageVerified](3334-incomingmessageverified.md)|詳細資訊|內送郵件已經過驗證。|安全性 ServiceModel|  
|[3335 - GetServiceInstanceStart](3335-getserviceinstancestart.md)|詳細資訊|服務執行個體擷取已啟動。|ServiceModel|  
|[3336 - GetServiceInstanceStop](3336-getserviceinstancestop.md)|詳細資訊|已擷取服務執行個體。|ServiceModel|  
|[3337 - ChannelReceiveStart](3337-channelreceivestart.md)|詳細資訊|ChannelHandlerId：%1 - 訊息接收迴圈已啟動。|通道|  
|[3338 - ChannelReceiveStop](3338-channelreceivestop.md)|詳細資訊|ChannelHandlerId：%1 - 訊息接收迴圈已停止。|通道|  
|[3339 - ChannelFactoryCreated](3339-channelfactorycreated.md)|詳細資訊|已建立 ChannelFactory。|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](3340-pipeconnectionacceptstart.md)|詳細資訊|管道連線接受已在 %1 上啟動。|通道|  
|[3341 - PipeConnectionAcceptStop](3341-pipeconnectionacceptstop.md)|詳細資訊|管道連線已接受。|通道|  
|[3342 - EstablishConnectionStart](3342-establishconnectionstart.md)|詳細資訊|已啟動 %1 的連線建立。|通道|  
|[3343 - EstablishConnectionStop](3343-establishconnectionstop.md)|詳細資訊|已建立連線。|通道|  
|[3345 - SessionPreambleUnderstood](3345-sessionpreambleunderstood.md)|詳細資訊|了解 '%1' 的工作階段前序編碼。|通道|  
|[3346 - ConnectionReaderSendFault](3346-connectionreadersendfault.md)|Error|連線讀取器正在傳送錯誤 '%1'。|通道|  
|[3347 - SocketAcceptClosed](3347-socketacceptclosed.md)|詳細資訊|通訊端接受已關閉。|TCP|  
|[3348 - ServiceHostFaulted](3348-servicehostfaulted.md)|重大|服務主機發生錯誤。|TCP|  
|[3349 - ListenerOpenStart](3349-listeneropenstart.md)|詳細資訊|開啟 '%1' 的接聽項。|通道|  
|[3350 - ListenerOpenStop](3350-listeneropenstop.md)|詳細資訊|接聽項開啟完成。|通道|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](3351-servermaxpooledconnectionsquotareached.md)|詳細資訊|達到伺服器最大的共用連線配額。|配額|  
|[3352 - TcpConnectionTimedOut](3352-tcpconnectiontimedout.md)|Error|遠端位址 %2 的 SocketId：%1 逾時。|TCP|  
|[3353 - TcpConnectionResetError](3353-tcpconnectionreseterror.md)|警告|遠端位址 %2 的 SocketId：%1 發生連線重設錯誤。|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](3354-servicesecuritynegotiationcompleted.md)|詳細資訊|服務安全性交涉已完成。|安全性|  
|[3355 - SecurityNegotiationProcessingFailure](3355-securitynegotiationprocessingfailure.md)|Error|安全性交涉處理失敗。|安全性|  
|[3356 - SecurityIdentityVerificationSuccess](3356-securityidentityverificationsuccess.md)|詳細資訊|安全性驗證成功。|安全性|  
|[3357 - SecurityIdentityVerificationFailure](3357-securityidentityverificationfailure.md)|Error|安全性驗證失敗。|安全性|  
|[3358 - PortSharingDuplicatedSocket](3358-portsharingduplicatedsocket.md)|詳細資訊|%1 的通訊端重複。|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](3359-securityimpersonationsuccess.md)|詳細資訊|安全性模擬成功。|安全性|  
|[3360 - SecurityImpersonationFailure](3360-securityimpersonationfailure.md)|警告|安全性模擬失敗。|安全性|  
|[3361 - HttpChannelRequestAborted](3361-httpchannelrequestaborted.md)|警告|HTTP 通道要求中止。|HTTP|  
|[3362 - HttpChannelResponseAborted](3362-httpchannelresponseaborted.md)|警告|HTTP 通道回應中止。|HTTP|  
|[3363 - HttpAuthFailed](3363-httpauthfailed.md)|警告|HTTP 驗證失敗。|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](3364-sharedlistenerproxyregisterstart.md)|詳細資訊|已啟動 URI '%1' 的 SharedListenerProxy 登錄。|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](3365-sharedlistenerproxyregisterstop.md)|詳細資訊|SharedListenerProxy 登錄停止。|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](3366-sharedlistenerproxyregisterfailed.md)|Error|SharedListenerProxy 登錄失敗，狀態為 '%1'。|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](3367-connectionpoolpreamblefailed.md)|Error|ConnectionPoolPreambleFailed。|通道|  
|[3368 - SslOnInitiateUpgrade](3368-ssloninitiateupgrade.md)|詳細資訊|SslOnAcceptUpgradeStart|安全性|  
|[3369 - SslOnAcceptUpgrade](3369-sslonacceptupgrade.md)|詳細資訊|SslOnAcceptUpgradeStop|安全性|  
|[3370 - BinaryMessageEncodingStart](3370-binarymessageencodingstart.md)|詳細資訊|BinaryMessageEncoder 開始編碼訊息。|通道|  
|[3371 - MtomMessageEncodingStart](3371-mtommessageencodingstart.md)|詳細資訊|MtomMessageEncoder 開始編碼訊息。|通道|  
|[3372 - TextMessageEncodingStart](3372-textmessageencodingstart.md)|詳細資訊|TextMessageEncoder 開始編碼訊息。|通道|  
|[3373 - BinaryMessageDecodingStart](3373-binarymessagedecodingstart.md)|詳細資訊|BinaryMessageEncoder 開始解碼訊息。|通道|  
|[3374 - MtomMessageDecodingStart](3374-mtommessagedecodingstart.md)|詳細資訊|MtomMessageEncoder 開始解碼訊息。|通道|  
|[3375 - TextMessageDecodingStart](3375-textmessagedecodingstart.md)|詳細資訊|TextMessageEncoder 開始解碼訊息。|通道|  
|[3376 - HttpResponseReceiveStart](3376-httpresponsereceivestart.md)|內容|HTTP 傳輸開始接收訊息。|HTTP|  
|[3377 - SocketReadStop](3377-socketreadstop.md)|詳細資訊|SocketId：%1 已讀取從 '%3' 讀取的 '%2' 個位元組。|TCP|  
|[3378 - SocketAsyncReadStop](3378-socketasyncreadstop.md)|詳細資訊|SocketId：%1 已讀取從 '%3' 讀取的 '%2' 個位元組。|TCP|  
|[3379 - SocketWriteStart](3379-socketwritestart.md)|詳細資訊|SocketId：%1 將 '%2' 個位元組寫入 '%3'。|TCP|  
|[3380 - SocketAsyncWriteStart](3380-socketasyncwritestart.md)|詳細資訊|SocketId：%1 將 '%2' 個位元組寫入 '%3'。|TCP|  
|[3381 - SequenceAcknowledgementSent](3381-sequenceacknowledgementsent.md)|詳細資訊|SessionId：%1 認可已傳送。|通道|  
|[3382 - ClientReliableSessionReconnect](3382-clientreliablesessionreconnect.md)|內容|SessionId：%1 重新連線中。|通道|  
|[3383 - ReliableSessionChannelFaulted](3383-reliablesessionchannelfaulted.md)|內容|SessionId：%1 發生錯誤。|通道|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](3384-windowsstreamsecurityoninitiateupgrade.md)|詳細資訊|WindowsStreamSecurity 正在初始化安全性升級。|安全性|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](3385-windowsstreamsecurityonacceptupgrade.md)|詳細資訊|Windows 接受升級的資料流安全性。|安全性|  
|[3386 - SocketConnectionAbort](3386-socketconnectionabort.md)|警告|SocketId：%1 正在中止。|TCP|  
|[3388 - HttpGetContextStart](3388-httpgetcontextstart.md)|詳細資訊|HttpGetContext 開始。|HTTP|  
|[3389 - ClientSendPreambleStart](3389-clientsendpreamblestart.md)|詳細資訊|用戶端傳送前序編碼開始。|通道|  
|[3390 - ClientSendPreambleStop](3390-clientsendpreamblestop.md)|詳細資訊|用戶端傳送前序編碼停止。|通道|  
|[3391 - HttpMessageReceiveFailed](3391-httpmessagereceivefailed.md)|警告|HTTP 訊息接收失敗。|HTTP|  
|[3392 - TransactionScopeCreate](3392-transactionscopecreate.md)|內容|TransactionScope 是以 LocalIdentifier：'%1' 和 DistributedIdentifier：'%2' 建立的。|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](3393-streamedmessagereadbyencoder.md)|內容|資料流訊息由編碼器讀取。|通道|  
|[3394 - StreamedMessageWrittenByEncoder](3394-streamedmessagewrittenbyencoder.md)|內容|資料流訊息由編碼器寫入。|通道|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](3395-messagewrittenasynchronouslybyencoder.md)|內容|編碼器將訊息寫入為非同步。|通道|  
|[3396 - BufferedAsyncWriteStart](3396-bufferedasyncwritestart.md)|內容|BufferId：%1 已完成寫入 '%2' 個位元組至基礎資料流。|通道|  
|[3397 - BufferedAsyncWriteStop](3397-bufferedasyncwritestop.md)|內容|編碼器將訊息寫入為非同步。|通道|  
|[3398 - PipeSharedMemoryCreated](3398-pipesharedmemorycreated.md)|詳細資訊|管線共用記憶體建立在 '%1'。|通道|  
|[3399 - NamedPipeCreated](3399-namedpipecreated.md)|詳細資訊|NamedPipe '%1' 已建立。|通道|  
|[3401 - SignatureVerificationStart](3401-signatureverificationstart.md)|詳細資訊|簽章驗證已啟動。|安全性|  
|[3402 - SignatureVerificationSuccess](3402-signatureverificationsuccess.md)|詳細資訊|簽章驗證成功。|安全性|  
|[3403 - WrappedKeyDecryptionStart](3403-wrappedkeydecryptionstart.md)|詳細資訊|已開始解密包裝的金鑰。|安全性|  
|[3404 - WrappedKeyDecryptionSuccess](3404-wrappedkeydecryptionsuccess.md)|詳細資訊|已成功解密包裝的金鑰。|安全性|  
|[3405 - EncryptedDataProcessingStart](3405-encrypteddataprocessingstart.md)|詳細資訊|已開始處理加密的資料。|安全性|  
|[3406 - EncryptedDataProcessingSuccess](3406-encrypteddataprocessingsuccess.md)|詳細資訊|已成功處理加密的資料。|安全性|  
|[3407 - HttpPipelineProcessInboundRequestStart](3407-httppipelineprocessinboundrequeststart.md)|詳細資訊|Http 訊息處理常式已開始處理輸入要求。|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](3408-httppipelinebeginprocessinboundrequeststart.md)|詳細資訊|Http 訊息處理常式已開始以非同步方式處理輸入要求。|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](3409-httppipelineprocessinboundrequeststop.md)|詳細資訊|Http 訊息處理常式已完成輸入要求的處理。|HTTP|  
|[3410 - HttpPipelineFaulted](3410-httppipelinefaulted.md)|警告|Http 訊息處理常式發生錯誤。|HTTP|  
|[3411 - HttpPipelineTimeoutException](3411-httppipelinetimeoutexception.md)|Error|WebSocket 連接逾時。|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](3412-httppipelineprocessresponsestart.md)|詳細資訊|Http 訊息處理常式已開始處理回應。|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](3413-httppipelinebeginprocessresponsestart.md)|詳細資訊|Http 訊息處理常式已開始以非同步方式處理回應。|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](3414-httppipelineprocessresponsestop.md)|詳細資訊|Http 訊息處理常式已完成回應的處理。|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](3415-websocketconnectionrequestsendstart.md)|詳細資訊|WebSocket 連接要求 '%1' 開始傳送。|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](3416-websocketconnectionrequestsendstop.md)|詳細資訊|WebSocketId：%1 已傳送連接要求。|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](3417-websocketconnectionacceptstart.md)|詳細資訊|WebSocket 開始接受連接。|HTTP|  
|[3418 - WebSocketConnectionAccepted](3418-websocketconnectionaccepted.md)|詳細資訊|WebSocketId：%1 已接受連接。|HTTP|  
|[3419 - WebSocketConnectionDeclined](3419-websocketconnectiondeclined.md)|Error|WebSocket 連接遭拒，狀態碼為 '%1'|HTTP|  
|[3420 - WebSocketConnectionFailed](3420-websocketconnectionfailed.md)|Error|WebSocket 連接要求失敗：'%1'|HTTP|  
|[3421 - WebSocketConnectionAborted](3421-websocketconnectionaborted.md)|Error|WebSocketId：%1 連接已中止。|HTTP|  
|[3422 - WebSocketAsyncWriteStart](3422-websocketasyncwritestart.md)|詳細資訊|WebSocketId：%1 將 '%2' 個位元組寫入 '%3'。|HTTP|  
|[3423 - WebSocketAsyncWriteStop](3423-websocketasyncwritestop.md)|詳細資訊|WebSocketId：%1 非同步寫入停止。|HTTP|  
|[3424 - WebSocketAsyncReadStart](3424-websocketasyncreadstart.md)|詳細資訊|WebSocketId：%1 開始讀取。|HTTP|  
|[3425 - WebSocketAsyncReadStop](3425-websocketasyncreadstop.md)|詳細資訊|WebSocketId：%1 從 '%3' 中讀取 '%2' 個位元組。|HTTP|  
|[3426 - WebSocketCloseSent](3426-websocketclosesent.md)|詳細資訊|WebSocketId：%1 將關閉訊息傳送至具有關閉狀態 '%3' 的 '%2'。|HTTP|  
|[3427 - WebSocketCloseOutputSent](3427-websocketcloseoutputsent.md)|詳細資訊|WebSocketId：%1 將關閉輸出訊息傳送至具有關閉狀態 '%3' 的 '%2'。|HTTP|  
|[3428 - WebSocketConnectionClosed](3428-websocketconnectionclosed.md)|詳細資訊|WebSocketId：%1 已關閉連接。|HTTP|  
|[3429 - WebSocketCloseStatusReceived](3429-websocketclosestatusreceived.md)|詳細資訊|WebSocketId：%1 收到具有狀態 '%2' 的連接關閉訊息。|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](3430-websocketuseversionfromclientwebsocketfactory.md)|詳細資訊|正在使用來自型別為 '%1' 的用戶端 WebSocket 工廠的 WebSocketVersion。|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](3431-websocketcreateclientwebsocketwithfactory.md)|詳細資訊|正在建立工廠型別 '%1' 的用戶端 WebSocket。|HTTP|  
|[3553 - XamlServicesLoadStart](3553-xamlservicesloadstart.md)|內容|XamlServicesLoad 開始|WebHost|  
|[3554 - XamlServicesLoadStop](3554-xamlservicesloadstop.md)|內容|XamlServicesLoad 停止|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](3555-createworkflowservicehoststart.md)|內容|CreateWorkflowServiceHost 開始|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](3556-createworkflowservicehoststop.md)|內容|CreateWorkflowServiceHost 停止|WebHost|  
|[3558 - ServiceActivationStart](3558-serviceactivationstart.md)|內容|服務啟用開始|WebHost|  
|[3559 - ServiceActivationStop](3559-serviceactivationstop.md)|內容|服務啟用停止|WebHost|  
|[3560 - ServiceActivationAvailableMemory](3560-serviceactivationavailablememory.md)|詳細資訊|可用的記憶體 (位元組)：%1|配額|  
|[3800 - RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|內容|路由服務正在關閉用戶端 '%1'。|RoutingServices|  
|[3800 - RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|警告|路由服務用戶端 '%1' 發生錯誤。|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](3802-routingservicecompletingoneway.md)|內容|路由服務單向訊息即將完成。|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](3803-routingserviceprocessingfailure.md)|Error|處理位址 '%1' 的端點上的訊息時，路由服務失敗。|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](3804-routingservicecreatingclientforendpoint.md)|內容|路由服務正在為下列端點建立用戶端：'%1'。|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](3805-routingservicedisplayconfig.md)|詳細資訊|路由服務已設定 RouteOnHeadersOnly：%1，SoapProcessingEnabled：%2，EnsureOrderedDispatch：%3。|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](3807-routingservicecompletingtwoway.md)|內容|路由服務要求回覆訊息即將完成。|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](3809-routingservicemessageroutedtoendpoints.md)|詳細資訊|路由服務將 ID：'%1' 的訊息傳送到 %2 端點清單。|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](3810-routingserviceconfigurationapplied.md)|內容|已對路由服務套用新的 RoutingConfiguration。|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](3815-routingserviceprocessingmessage.md)|內容|路由服務正在處理訊息，ID：'%1'，動作：'%2'，輸入 URL：'%3'，接收於異動：%4。|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](3816-routingservicetransmittingmessage.md)|內容|路由服務正在將 ID 為：'%1' [作業%2] 的訊息傳輸至 '%3'。|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](3817-routingservicecommittingtransaction.md)|內容|路由服務正在認可下列 ID 的異動：'%1'。|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](3818-routingserviceduplexcallbackexception.md)|Error|路由服務元件 %1 遇到雙工回呼例外狀況。|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](3819-routingservicemovedtobackup.md)|內容|ID：'%1' 的路由服務訊息 [作業 %2] 已移到備份端點 '%3'。|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](3820-routingservicecreatingtransaction.md)|內容|路由服務為處理訊息，已建立 ID 為 '%1' 的新異動。|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](3821-routingserviceclosefailed.md)|警告|關閉傳出用戶端 '%1' 時路由服務失敗。|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](3822-routingservicesendingresponse.md)|內容|路由服務正在傳回動作為 '%1' 的回應訊息。|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](3823-routingservicesendingfaultresponse.md)|警告|路由服務正在傳回動作為 '%1' 的錯誤回應訊息。|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](3824-routingservicecompletingreceivecontext.md)|詳細資訊|路由服務正在為 ID：'%1' 的訊息呼叫 ReceiveContext.Complete。|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](3825-routingserviceabandoningreceivecontext.md)|警告|路由服務正在為 ID 為 '%1' 的訊息呼叫 ReceiveContext.Abandon。|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](3826-routingserviceusingexistingtransaction.md)|詳細資訊|路由服務會使用現有的異動 '%1' 傳送訊息。|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](3827-routingservicetransmitfailed.md)|警告|傳送至 '%1' 時，路由服務失敗。|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](3828-routingservicefiltertablematchstart.md)|內容|路由服務 MessageFilterTable 比對開始。|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](3829-routingservicefiltertablematchstop.md)|內容|路由服務 MessageFilterTable 比對停止。|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](3830-routingserviceabortingchannel.md)|詳細資訊|路由服務正在通道：'%1' 上呼叫中止。|RoutingServices|  
|[3831 - RoutingServiceHandledException](3831-routingservicehandledexception.md)|詳細資訊|路由服務已經處理過例外狀況。|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](3832-routingservicetransmitsucceeded.md)|內容|路由服務成功地將 ID：'%1 的訊息 [作業 %2] 傳輸至 '%3'。|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](4001-transportlistenersessionsreceived.md)|詳細資訊|透過 '%1' 與傳輸接聽項工作階段一起接收|ActivationServices|  
|[4002 - FailFastException](4002-failfastexception.md)|重大|FailFastException。|ActivationServices|  
|[4003 - ServiceStartPipeError](4003-servicestartpipeerror.md)|Error|服務啟動管道時發生錯誤。|ActivationServices|  
|[4008 - DispatchSessionStart](4008-dispatchsessionstart.md)|詳細資訊|工作階段分派已啟動。|ActivationServices|  
|[4008 - DispatchSessionStart](4008-dispatchsessionstart.md)|警告|'%1' 的工作階段分派失敗，因為擱置中的工作階段佇列已填滿 '%2' 擱置中的項目。|ActivationServices|  
|[4011 - MessageQueueRegisterStart](4011-messagequeueregisterstart.md)|詳細資訊|訊息佇列登錄開始。|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](4012-messagequeueregisterabort.md)|Error|URI：'%2' 的訊息佇列登錄已中止，狀態為：'%1'。|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](4013-messagequeueunregistersucceeded.md)|詳細資訊|為 URI：'%1' 解除登錄訊息佇列成功。|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](4014-messagequeueregisterfailed.md)|Error|URI：'%1' 的訊息佇列登錄失敗，狀態為：'%2'。|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](4015-messagequeueregistercompleted.md)|內容|URI '%1' 的訊息佇列登錄已完成。|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](4016-messagequeueduplicatedsocketerror.md)|Error|訊息佇列無法複製通訊端。|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](4019-messagequeueduplicatedsocketcomplete.md)|詳細資訊|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](4020-tcptransportlistenerlisteningstart.md)|詳細資訊|開始在 URI：'%1' 上接聽 Tcp 傳輸接聽項。|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](4021-tcptransportlistenerlisteningstop.md)|詳細資訊|TCP 傳輸接聽項正在接聽。|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](4022-webhostunregisterprotocolfailed.md)|Error|錯誤碼：%1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](4023-wasclosealllistenerchannelinstancescompleted.md)|內容|已關閉所有完成的接聽項通道執行個體。|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](4024-wasclosealllistenerchannelinstancesfailed.md)|Error|錯誤碼：%1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](4025-openlistenerchannelinstancefailed.md)|Error|錯誤碼：%1|ActivationServices|  
|[4026 - WasConnected](4026-wasconnected.md)|詳細資訊|WAS 已連線。|ActivationServices|  
|[4027 - WasDisconnected](4027-wasdisconnected.md)|詳細資訊|WAS 已中斷連線。|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](4028-pipetransportlistenerlisteningstart.md)|詳細資訊|uri：%1 上的管線傳輸接聽項接聽開始。|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](4029-pipetransportlistenerlisteningstop.md)|詳細資訊|管道傳輸接聽項接聽停止。|ActivationServices|  
|[4030 - DispatchSessionSuccess](4030-dispatchsessionsuccess.md)|內容|工作階段分派成功。|ActivationServices|  
|[4031 - DispatchSessionFailed](4031-dispatchsessionfailed.md)|Error|工作階段分派失敗。|ActivationServices|  
|[4032 - WasConnectionTimedout](4032-wasconnectiontimedout.md)|重大|WAS 連線逾時。|ActivationServices|  
|[4033 - RoutingTableLookupStart](4033-routingtablelookupstart.md)|詳細資訊|路由表查閱已啟動。|ActivationServices|  
|[4034 - RoutingTableLookupStop](4034-routingtablelookupstop.md)|詳細資訊|路由表查閱已完成。|ActivationServices|  
|[4035 - PendingSessionQueueRatio](4035-pendingsessionqueueratio.md)|詳細資訊|擱置中的工作階段佇列比例：%1/%2|配額|  
|[4600 - MessageLogEventSizeExceeded](4600-messagelogeventsizeexceeded.md)|警告|無法記錄訊息，因為它已超過 ETW 事件大小|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](4801-discoveryclientinclientchannelfailedtoclose.md)|警告|在 DiscoveryClientChannel 中建立的 DiscoveryClient 無法關閉，因此已經中止。|探索|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](4802-discoveryclientprotocolexceptionsuppressed.md)|內容|ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的。 這可能是因為 DiscoveryService 仍在嘗試傳送回應給 DiscoveryClient。|探索|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](4803-discoveryclientreceivedmulticastsuppression.md)|內容|DiscoveryClient 收到來自 DiscoveryProxy 的多點傳送隱藏訊息。|探索|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](4804-discoverymessagereceivedafteroperationcompleted.md)|內容|messageId='%2' 的 %1 訊息已由 DiscoveryClient 丟棄，因為對應的 %3 作業已完成。|探索|  
|[4805 - DiscoveryMessageWithInvalidContent](4805-discoverymessagewithinvalidcontent.md)|警告|一項 messageId='%2' 的 %1 訊息已遭丟棄，因為它的內容無效。|探索|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|警告|messageId='%2' 且 relatesTo='%3' 的 %1 訊息已由 DiscoveryClient 丟棄，因為對應的 %4 作業已完成，或是 relatesTo 值無效。|探索|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](4807-discoverymessagewithinvalidreplyto.md)|警告|messageId='%1' 的探索要求訊息已遭丟棄，因為它的 ReplyTo 地址無效。|探索|  
|[4808 - DiscoveryMessageWithNoContent](4808-discoverymessagewithnocontent.md)|警告|%1 訊息已遭丟棄，因為它沒有任何內容。|探索|  
|[4809 - DiscoveryMessageWithNullMessageId](4809-discoverymessagewithnullmessageid.md)|警告|%1 訊息已遭丟棄，因為訊息標頭未包含必要的 MessageId 屬性。|探索|  
|[4810 - DiscoveryMessageWithNullMessageSequence](4810-discoverymessagewithnullmessagesequence.md)|警告|messageId='%2' 的 %1 訊息已遭 DiscoveryClient 丟棄，因為它沒有 DiscoveryMessageSequence 屬性。|探索|  
|[4811 - DiscoveryMessageWithNullRelatesTo](4811-discoverymessagewithnullrelatesto.md)|警告|messageId='%2' 的 %1 訊息已遭 DiscoveryClient 丟棄，因為訊息標頭未包含必要的 RelatesTo 屬性。|探索|  
|[4812 - DiscoveryMessageWithNullReplyTo](4812-discoverymessagewithnullreplyto.md)|警告|messageId='%1' 的探索要求訊息已遭丟棄，因為它沒有 ReplyTo 地址。|探索|  
|[4813 - DuplicateDiscoveryMessage](4813-duplicatediscoverymessage.md)|警告|messageId='%2' 的 %1 訊息已遭丟棄，因為它是重複項目。|探索|  
|[4814 - EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|內容|EndpointAddress='%1' 且 ListenUri='%2' 的端點可搜尋性已遭停用。|探索|  
|[4814 - EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|內容|EndpointAddress='%1' 且 ListenUri='%2' 的端點可搜尋性已經啟用。|探索|  
|[4816 - FindInitiatedInDiscoveryClientChannel](4816-findinitiatedindiscoveryclientchannel.md)|詳細資訊|DiscoveryClientChannel 中已初始化尋找作業以探索端點。|探索|  
|[4817 - InnerChannelCreationFailed](4817-innerchannelcreationfailed.md)|警告|DiscoveryClientChannel 無法以 EndpointAddress='%1' 且 Via='%2' 的探索結果端點建立通道。 DiscoveryClientChannel 現在將嘗試使用下一個可用的探索結果端點。|探索|  
|[4818 - InnerChannelOpenFailed](4818-innerchannelopenfailed.md)|警告|DiscoveryClientChannel 無法以 EndpointAddress='%1' 且 Via='%2' 的探索結果端點開啟通道。 DiscoveryClientChannel 現在將嘗試使用下一個可用的探索結果端點。|探索|  
|[4819 - InnerChannelOpenSucceeded](4819-innerchannelopensucceeded.md)|內容|DiscoveryClientChannel 成功發現一個端點並使用它開啟通道。 用戶端已使用 EndpointAddress='%1' 和 Via='%2' 連接至服務。|探索|  
|[4820 - SynchronizationContextReset](4820-synchronizationcontextreset.md)|內容|SynchronizationContext 已由 DiscoveryClientChannel 重設為其原始值 %1。|探索|  
|[4821 - SynchronizationContextSetToNull](4821-synchronizationcontextsettonull.md)|內容|在初始化尋找作業之前，SynchronizationContext 已由 DiscoveryClientChannel 設定為 null。|探索|  
|[5001 - DCSerializeWithSurrogateStart](5001-dcserializewithsurrogatestart.md)|詳細資訊|DataContract 使用代理序列化 %1 開始。|序列化|  
|[5002 - DCSerializeWithSurrogateStop](5002-dcserializewithsurrogatestop.md)|詳細資訊|DataContract 使用代理序列化停止。|序列化|  
|[5003 - DCDeserializeWithSurrogateStart](5003-dcdeserializewithsurrogatestart.md)|詳細資訊|DataContract 使用代理還原序列化 %1 開始。|序列化|  
|[5004 - DCDeserializeWithSurrogateStop](5004-dcdeserializewithsurrogatestop.md)|詳細資訊|DataContract 使用代理還原序列化停止。|序列化|  
|[5005 - ImportKnownTypesStart](5005-importknowntypesstart.md)|詳細資訊|ImportKnownTypes 開始。|序列化|  
|[5006 - ImportKnownTypesStop](5006-importknowntypesstop.md)|詳細資訊|ImportKnownTypes 停止。|序列化|  
|[5007 - DCResolverResolve](5007-dcresolverresolve.md)|詳細資訊|解析 %1 的 DataContract 解析程式開始。|序列化|  
|[5008 - DCGenWriterStart](5008-dcgenwriterstart.md)|詳細資訊|DataContract 產生 %2 的 %1 寫入器開始。|序列化|  
|[5009 - DCGenWriterStop](5009-dcgenwriterstop.md)|詳細資訊|DataContract 產生寫入器停止。|序列化|  
|[5010 - DCGenReaderStart](5010-dcgenreaderstart.md)|詳細資訊|DataContract 產生 %2 的 %1 讀取器開始。|序列化|  
|[5011 - DCGenReaderStop](5011-dcgenreaderstop.md)|詳細資訊|DataContract 產生停止。|序列化|  
|[5012 - DCJsonGenReaderStart](5012-dcjsongenreaderstart.md)|詳細資訊|Json 產生 %2 的 %1 讀取器開始。|序列化|  
|[5013 - DCJsonGenReaderStop](5013-dcjsongenreaderstop.md)|詳細資訊|Json 讀取器產生停止。|序列化|  
|[5014 - DCJsonGenWriterStart](5014-dcjsongenwriterstart.md)|詳細資訊|Json 產生 %2 的 %1 寫入器開始。|序列化|  
|[5015 - DCJsonGenWriterStop](5015-dcjsongenwriterstop.md)|詳細資訊|Json 產生寫入器停止。|序列化|  
|[5016 - GenXmlSerializableStart](5016-genxmlserializablestart.md)|詳細資訊|'%1' 的產生 Xml 可序列化開始。|序列化|  
|[5017 - GenXmlSerializableStop](5017-genxmlserializablestop.md)|詳細資訊|產生 Xml 可序列化停止。|序列化|  
|[5203 - JsonMessageDecodingStart](5203-jsonmessagedecodingstart.md)|詳細資訊|JsonMessageEncoder 開始解碼訊息。|通道|  
|[5204 - JsonMessageEncodingStart](5204-jsonmessageencodingstart.md)|詳細資訊|JsonMessageEncoder 開始編碼訊息。|通道|  
|[5402 - TokenValidationStarted](5402-tokenvalidationstarted.md)|詳細資訊|SecurityToken (類型 '%1' 和 ID '%2') 驗證已開始。|安全性|  
|[5403 - TokenValidationSuccess](5403-tokenvalidationsuccess.md)|詳細資訊|SecurityToken (類型 '%1' 和 ID '%2') 驗證成功。|安全性|  
|[5404 - TokenValidationFailure](5404-tokenvalidationfailure.md)|Error|SecurityToken (類型 '%1' 和 ID '%2') 驗證失敗。 %3|安全性|  
|[5405 - GetIssuerNameSuccess](5405-getissuernamesuccess.md)|詳細資訊|擷取 tokenId：%2 中的簽發者名稱：%1 成功。|安全性|  
|[5406 - GetIssuerNameFailure](5406-getissuernamefailure.md)|Error|擷取 tokenId：%1 中的簽發者名稱失敗。|安全性|  
|[5600 - FederationMessageProcessingStarted](5600-federationmessageprocessingstarted.md)|詳細資訊|已開始處理同盟訊息。|安全性|  
|[5601 - FederationMessageProcessingSuccess](5601-federationmessageprocessingsuccess.md)|詳細資訊|已成功處理同盟訊息。|安全性|  
|[5602 - FederationMessageCreationStarted](5602-federationmessagecreationstarted.md)|詳細資訊|正在從啟動的表單張貼建立同盟訊息。|安全性|  
|[5603 - FederationMessageCreationSuccess](5603-federationmessagecreationsuccess.md)|詳細資訊|已成功從表單張貼建立同盟訊息。|安全性|  
|[5604 - SessionCookieReadingStarted](5604-sessioncookiereadingstarted.md)|詳細資訊|已開始從工作階段 Cookie 讀取工作階段權杖。|安全性|  
|[5605 - SessionCookieReadingSuccess](5605-sessioncookiereadingsuccess.md)|詳細資訊|已成功從工作階段 Cookie 讀取工作階段權杖。|安全性|  
|[5606 - PrincipalSettingFromSessionTokenStarted](5606-principalsettingfromsessiontokenstarted.md)|詳細資訊|已開始從工作階段權杖設定主體。|安全性|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](5607-principalsettingfromsessiontokensuccess.md)|詳細資訊|已成功從工作階段權杖設定主體。|安全性|  
|[57393 - AppDomainUnload](57393-appdomainunload.md)|內容|AppDomain 卸載。 AppDomain.FriendlyName %1、ProcessName %2、ProcessId %3。|基礎結構|  
|[57394 - HandledException](57394-handledexception.md)|內容|正在處理例外狀況。|基礎結構|  
|[57395 - ShipAssertExceptionMessage](57395-shipassertexceptionmessage.md)|Error|發生未預期的失敗。 應用程式不應該嘗試處理此錯誤。 為方便診斷，這個英文訊息與下列失敗相關：%1。|基礎結構|  
|[57396 - ThrowingException](57396-throwingexception.md)|警告|正在擲回例外狀況。 來源 %1。|基礎結構|  
|[57397 - UnhandledException](57397-unhandledexception.md)|重大|未處理的例外狀況。|基礎結構|  
|[57399 - TraceCodeEventLogCritical](57399-tracecodeeventlogcritical.md)|重大|已寫入 EventLog。|基礎結構|  
|[57400 - TraceCodeEventLogError](57400-tracecodeeventlogerror.md)|Error|已寫入 EventLog。|基礎結構|  
|[57401 - TraceCodeEventLogInfo](57401-tracecodeeventloginfo.md)|內容|已寫入 EventLog。|基礎結構|  
|[57402 - TraceCodeEventLogVerbose](57402-tracecodeeventlogverbose.md)|詳細資訊|已寫入 EventLog。|基礎結構|  
|[57403 - TraceCodeEventLogWarning](57403-tracecodeeventlogwarning.md)|警告|已寫入 EventLog。|基礎結構|  
|[57404 - HandledExceptionWarning](57404-handledexceptionwarning.md)|警告|正在處理例外狀況。|基礎結構|  
|[62326 - HttpHandlerPickedForUrl](62326-httphandlerpickedforurl.md)|內容|URL '%1' 裝載了具有根元素型別 '%2' 的 XAML 文件。 系統挑選 HTTP 處理常式型別 '%3' 來服務對這個 URL 提出的所有要求。|WebHost|
