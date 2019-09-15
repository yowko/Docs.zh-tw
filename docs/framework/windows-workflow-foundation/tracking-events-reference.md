---
title: 追蹤事件參考
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: af0c4441b89345b67c46c714d9ab3e5ceb9e3d6f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988973"
---
# <a name="tracking-events-reference"></a>追蹤事件參考
在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中執行工作流程期間，會引發追蹤事件，因為工作流程會通過生命週期的各種階段。 主機可訂閱這些事件，並保持工作流程在其生命週期時的進度狀態更新。 本節中將討論引發的追蹤事件。  
  
## <a name="event-reference"></a>事件參考  
  
|事件 ID|事件層級|事件訊息|關鍵字|  
|--------------|-----------------|-------------------|--------------|  
|[100 - WorkflowInstanceRecord](100-workflowinstancerecord.md)|內容|TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[101 - WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Error|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName=%8, Exception=%9, Annotations= %10, ProfileName = %11|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[102 - WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|警告|TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[103 - ActivityStateRecord](103-activitystaterecord.md)|內容|TrackRecord = ActivityStateRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, State = %4, Name=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Arguments=%9, Variables=%10, Annotations=%11, ProfileName = %12|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[104 - ActivityScheduledRecord](104-activityscheduledrecord.md)|內容|TrackRecord = ActivityScheduledRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、Name = %4、ActivityId = %5、ActivityInstanceId = %6、ActivityTypeName = %7、ChildActivityName = %8、ChildActivityId = %9、ChildActivityInstanceId = %10、ChildActivityTypeName =%11、Annotations=%12、ProfileName = %13|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[105 - FaultPropagationRecord](105-faultpropagationrecord.md)|警告|TrackRecord = FaultPropagationRecord、InstanceID=%1、RecordNumber=%2、EventTime=%3、FaultSourceActivityName=%4、FaultSourceActivityId=%5、FaultSourceActivityInstanceId=%6、FaultSourceActivityTypeName=%7、FaultHandlerActivityName=%8、FaultHandlerActivityId = %9、FaultHandlerActivityInstanceId =%10、FaultHandlerActivityTypeName=%11、Fault=%12、IsFaultSource=%13、Annotations=%14、ProfileName = %15|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[106 - CancelRequestRecord](106-cancelrequestrecord.md)|內容|TrackRecord = CancelRequestedRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityId=%5, ActivityInstanceId=%6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = %10, ChildActivityTypeName =%11, Annotations=%12, ProfileName = %13|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[107 -- BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|內容|TrackRecord = BookmarkResumptionRecord、InstanceID=%1、RecordNumber=%2,EventTime=%3、Name=%4、SubInstanceID=%5、OwnerActivityName=%6、OwnerActivityId =%7、OwnerActivityInstanceId=%8、OwnerActivityTypeName=%9、Annotations=%10、ProfileName = %11|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[108 - CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|內容|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[110 - CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|警告|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[111 - CustomTrackingRecordError](111-customtrackingrecorderror.md)|Error|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[112 - WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|內容|TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[113 - WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Error|TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[114 - WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|內容|TrackRecord= WorkflowInstanceRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8|HealthMonitoring、WFTracking|  
|[115 - WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|警告|TrackRecord = WorkflowInstanceAbortedRecord、InstanceID =% 1、RecordNumber =% 2、EventTime =% 3、ActivityDefinitionId =% 4、Reason =% 5、注釋 =% 6、ProfileName =% 7、WorkflowDefinitionIdentity =% 8|HealthMonitoring、WFTracking|  
|[116 - WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|內容|TrackRecord = WorkflowInstanceSuspendedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8|HealthMonitoring、WFTracking|  
|[117 - WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Error|TrackRecord = WorkflowInstanceTerminatedRecord、InstanceID =% 1、RecordNumber =% 2、EventTime =% 3、ActivityDefinitionId =% 4、Reason =% 5、注釋 =% 6、ProfileName =% 7、WorkflowDefinitionIdentity =% 8|HealthMonitoring、WFTracking|  
|[118 - WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Error|TrackRecord = WorkflowInstanceUnhandledExceptionRecord、InstanceID =% 1、RecordNumber =% 2、EventTime =% 3、ActivityDefinitionId =% 4、錯誤識別碼 =% 5、SourceId =% 6、SourceInstanceId =% 7、SourceTypeName =% 8、Exception =% 9、注釋 =% 10、ProfileName =% 11，WorkflowDefinitionIdentity =% 12|HealthMonitoring、WFTrackingHealthMonitoring、WFTracking|  
|[119 - WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|內容|TrackRecord= WorkflowInstanceUpdatedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、OriginalDefinitionIdentity = %6、UpdatedDefinitionIdentity = %7、Annotations = %8、ProfileName = %9|HealthMonitoring、WFTracking|  
|[225 - TraceCorrelationKeys](225-tracecorrelationkeys.md)|內容|在父範圍 '%3' 中使用 '%2' 值計算的相互關聯索引鍵 '%1'。|疑難排解 WFServices|  
|[440 - StartSignpostEvent1](440-startsignpostevent.md)|內容|活動界限。|疑難排解 WFServices|  
|[441- StopSignpostEvent1](441-stopsignpostevent.md)|內容|活動界限。|疑難排解 WFServices|  
|[1001 - WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|內容|WorkflowInstance Id：'%1' 已在 Closed 狀態中完成。|WFRuntime|  
|[1002 - WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|內容|WorkflowApplication Id：'%1' 已終止。 它已經以 Faulted 狀態完成，並發生例外狀況。|WFRuntime|  
|[1003 - WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|內容|WorkflowInstance Id：'%1' 已在 Canceled 狀態中完成。|WFRuntime|  
|[1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|內容|WorkflowInstance Id：'%1' 已中止，並發生例外狀況。|WFRuntime|  
|[1005 - WorkflowApplicationIdled](1005-workflowapplicationidled.md)|內容|WorkflowApplication Id：'%1' 閒置。|WFRuntime|  
|[1006 - WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Error|WorkflowInstance 識別碼： '% 1 ' 發生未處理的例外狀況。  例外狀況源自活動 '% 2 '、DisplayName： '% 3 '。  將採取下列動作：% 4。|WFRuntime|  
|[1007 - WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|內容|WorkflowApplication Id：'%1' 是永續性的。|WFRuntime|  
|[1008 - WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|內容|WorkflowInstance Id：'%1' 已卸載。|WFRuntime|  
|[1009 - ActivityScheduled](1009-activityscheduled.md)|內容|父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程子活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。|WFRuntime|  
|[1010 - ActivityCompleted](1010-activitycompleted.md)|內容|父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程子活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。|WFRuntime|  
|[1011 - ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|詳細資訊|已經為活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 排程 ExecuteActivityWorkItem。|WFRuntime|  
|[1012 - StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|詳細資訊|開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。|WFRuntime|  
|[1013 - CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|詳細資訊|已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 ExecuteActivityWorkItem。|WFRuntime|  
|[1014 - ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|詳細資訊|已排程父活動 '% 1 '、DisplayName： '% 2 '、InstanceId： '% 3 ' 的 CompletionWorkItem。  已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。|WFRuntime|  
|[1015 - StartCompletionWorkItem](1015-startcompletionworkitem.md)|詳細資訊|開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。 已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。|WFRuntime|  
|[1016 - CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|詳細資訊|已完成父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。 已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。|WFRuntime|  
|[1017 - ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|詳細資訊|已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。|WFRuntime|  
|[1018 - StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|詳細資訊|開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3'的 CancelActivityWorkItem。|WFRuntime|  
|[1019 - CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|詳細資訊|已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CancelActivityWorkItem。|WFRuntime|  
|[1020 - CreateBookmark](1020-createbookmark.md)|詳細資訊|已經為活動 '% 1 '、DisplayName： '% 2 '、InstanceId： '% 3 ' 建立書簽。  BookmarkName：%4、BookmarkScope：%5。|WFRuntime|  
|[1021 - ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|詳細資訊|已排程活動 '% 1 '、DisplayName： '% 2 '、InstanceId： '% 3 ' 的 BookmarkWorkItem。  BookmarkName：%4、BookmarkScope：%5。|WFRuntime|  
|[1022 - StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|詳細資訊|開始執行活動 '% 1 '、DisplayName： '% 2 '、InstanceId： '% 3 ' 的 BookmarkWorkItem。  BookmarkName：%4、BookmarkScope：%5。|WFRuntime|  
|[1023 - CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|詳細資訊|已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 BookmarkWorkItem。 BookmarkName：%4、BookmarkScope：%5。|WFRuntime|  
|[1024 - CreateBookmarkScope](1024-createbookmarkscope.md)|詳細資訊|已建立 BookmarkScope：%1。|WFRuntime|  
|[1025 - BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|詳細資訊|已用 ID：'%2' 初始化具有 TemporaryId：'%1' 的 BookmarkScope。|WFRuntime|  
|[1026 - ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|詳細資訊|已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。|WFRuntime|  
|[1027 - StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|詳細資訊|開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。|WFRuntime|  
|[1028 - CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|詳細資訊|已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。|WFRuntime|  
|[1029 - ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|詳細資訊|已排程活動 '% 1 '、DisplayName： '% 2 '、InstanceId： '% 3 ' 的 FaultWorkItem。  活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。|WFRuntime|  
|[1030 - StartFaultWorkItem](1030-startfaultworkitem.md)|詳細資訊|開始執行活動 '% 1 '、DisplayName： '% 2 '、InstanceId： '% 3 ' 的 FaultWorkItem。  活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。|WFRuntime|  
|[1031 - CompleteFaultWorkItem](1031-completefaultworkitem.md)|詳細資訊|已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。 活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。|WFRuntime|  
|[1032 - ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|詳細資訊|已排定活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。|WFRuntime|  
|[1033 - StartRuntimeWorkItem](1033-startruntimeworkitem.md)|詳細資訊|開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。|WFRuntime|  
|[1034 - CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|詳細資訊|已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的執行階段工作項目。|WFRuntime|  
|[1035 - RuntimeTransactionSet](1035-runtimetransactionset.md)|詳細資訊|活動 '% 1 '、DisplayName： '% 2 '、InstanceId： '% 3 ' 已設定執行時間交易。  執行已隔離到活動 '% 4 '、DisplayName： '% 5 '、InstanceId： '% 6 '。|WFRuntime|  
|[1036 - RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|詳細資訊|活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程完成執行階段異動。|WFRuntime|  
|[1037 - RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|詳細資訊|執行階段異動已完成，狀態為 '%1'。|WFRuntime|  
|[1038 - EnterNoPersistBlock](1038-enternopersistblock.md)|詳細資訊|正在進入無持續性區塊。|WFRuntime|  
|[1039 - ExitNoPersistBlock](1039-exitnopersistblock.md)|詳細資訊|正在結束無持續性區塊。|WFRuntime|  
|[1040 - InArgumentBound](1040-inargumentbound.md)|詳細資訊|活動 '%2'、DisplayName：'%3'、InstanceId：'%4' 中的引數 '%1' 已與值 %5 繫結。|WFActivities|  
|[1041 - WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|內容|WorkflowApplication 識別碼： '% 1 ' 為閒置和永久性。  將採取下列動作：% 2。|WFRuntime|  
|[1101 - WorkflowActivityStart](1101-workflowactivitystart.md)|內容|WorkflowInstance Id：'%1' E2E 活動|WFRuntime|  
|[1102 - WorkflowActivityStop](1102-workflowactivitystop.md)|內容|WorkflowInstance Id：'%1' E2E 活動|WFRuntime|  
|[1103 - WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|內容|WorkflowInstance Id：'%1' E2E 活動|WFRuntime|  
|[1104 - WorkflowActivityResume](1104-workflowactivityresume.md)|內容|WorkflowInstance Id：'%1' E2E 活動|WFRuntime|  
|[1124 - InvokeMethodIsStatic](1124-invokemethodisstatic.md)|內容|InvokeMethod '%1' - 方法是靜態方法。|WFRuntime|  
|[1125 - InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|內容|InvokeMethod '%1' - 方法不是靜態方法。|WFRuntime|  
|[1126 - InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|內容|在活動 '%1' 呼叫的方法中發生例外狀況。 %2|WFRuntime|  
|[1131 - InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|內容|InvokeMethod '%1' - 方法使用 '%2' 和 '%3' 非同步模式。|WFRuntime|  
|[1132 - InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|內容|InvokeMethod '%1' - 方法未使用非同步模式。|WFRuntime|  
|[1140 - FlowchartStart](1140-flowchartstart.md)|內容|流程圖 '%1' - 已排程 Start。|WFActivities|  
|[1141 - FlowchartEmpty](1141-flowchartempty.md)|警告|流程圖 '%1' - 已執行，但沒有任何節點。 在活動 '%1' 呼叫的方法中發生例外狀況。 %2|WFActivities|  
|[1143 - FlowchartNextNull](1143-flowchartnextnull.md)|內容|流程圖 '%1'/FlowStep - 下一個節點是 null。 流程圖執行將結束。|WFActivities|  
|[1146 - FlowchartSwitchCase](1146-flowchartswitchcase.md)|內容|流程圖 '%1'/FlowSwitch - 已選取案例 '%2'。|WFActivities|  
|[1147 - FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|內容|流程圖 '%1'/FlowSwitch - 已選取預設案例。|WFActivities|  
|[1148 - FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|內容|流程圖 '%1'/FlowSwitch - 找不到符合運算式結果的案例活動或預設案例。 流程圖執行將結束。|WFActivities|  
|[1150 - CompensationState](1150-compensationstate.md)|內容|CompensableActivity '%1' 處於 '%2' 狀態。|WFActivities|  
|[1223 - SwitchCaseNotFound](1223-switchcasenotfound.md)|內容|Switch 活動 '%1' 找不到符合運算式結果的 Case 活動。|WFActivities|  
|[1449 - WfMessageReceived](1449-wfmessagereceived.md)|內容|工作流程所接收的訊息|WFServices|  
|[1450 - WfMessageSent](1450-wfmessagesent.md)|內容|從工作流程傳送的訊息|WFServices|  
|[2021 - ExecuteWorkItemStart](2021-executeworkitemstart.md)|詳細資訊|執行工作項目開始|WFRuntime|  
|[2022 - ExecuteWorkItemStop](2022-executeworkitemstop.md)|詳細資訊|執行工作項目停止|WFRuntime|  
|[2023 - SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|詳細資訊|SendMessageChannelCache 遺漏|WFRuntime|  
|[2024 - InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|詳細資訊|活動 '%1' 上的 InternalCacheMetadata 已啟動。|WFRuntime|  
|[2025 - InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|詳細資訊|活動 '%1' 上的 InternalCacheMetadata 已停止。|WFRuntime|  
|[2026 - CompileVbExpressionStart](2026-compilevbexpressionstart.md)|詳細資訊|編譯 VB 運算式 '%1'|WFRuntime|  
|[2027 - CacheRootMetadataStart](2027-cacherootmetadatastart.md)|詳細資訊|活動 '%1' 上的 CacheRootMetadata 已啟動|WFRuntime|  
|[2028 - CacheRootMetadataStop](2028-cacherootmetadatastop.md)|詳細資訊|活動 %1 上的 CacheRootMetadata 已停止。|WFRuntime|  
|[2029 - CompileVbExpressionStop](2029-compilevbexpressionstop.md)|詳細資訊|完成編譯 VB 運算式。|WFRuntime|  
|[2576 - TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|內容|TryCatch 活動 '%1' 攔截到型別 '%2' 的例外狀況。|WFActivities|  
|[2577 - TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|警告|TryCatch 活動 '%1' 的子活動在取消期間擲回例外狀況。|WFActivities|  
|[2578 - TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|警告|與 TryCatch 活動 '%1' 關聯的 Catch 或 Finally 活動擲回例外狀況。|WFActivities|  
|[3501 - InferredContractDescription](3501-inferredcontractdescription.md)|內容|已從 WorkflowService 推斷出 Name='%1' 且 Namespace='%2' 的 ContractDescription。|WFServices|  
|[3502 - InferredOperationDescription](3502-inferredoperationdescription.md)|內容|已從 WorkflowService 推斷出合約 '%2' 中 Name='%1' 的 OperationDescription。 IsOneWay=%3。|WFServices|  
|[3503 - DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|警告|發現 Where='%1' 的重複 CorrelationQuery。 計算相互關聯時不會使用這個重複的查詢。|WFServices|  
|[3507 - ServiceEndpointAdded](3507-serviceendpointadded.md)|內容|已經針對位址 '%1'、繫結 '%2' 和合約 '%3' 加入服務端點。|WFServices|  
|[3508 - TrackingProfileNotFound](3508-trackingprofilenotfound.md)|詳細資訊|找不到 ActivityDefinitionId '%2' 的 TrackingProfile '%1'。 在組態檔中找不到 TrackingProfile，或者 ActivityDefinitionId 不相符。|WFServices|  
|[3550 - BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|內容|目前無法執行作業 '%1'。 將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。|WFServices|  
|[3551 - BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|內容|目前無法在服務執行個體 '%1' 上執行作業 '%2'。 將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。|WFServices|  
|[3552 - MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|警告|已達到 '% 1 ' 的節流 ' MaxPendingMessagesPerChannel ' 限制。 若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。|配額 WFServices|  
|[3557 - TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|內容|呼叫 ID = '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。|WFServices|  
|[4201 - EndSqlCommandExecute](4201-endsqlcommandexecute.md)|詳細資訊|結束 SQL 命令執行：%1|WFInstanceStore|  
|[4202 - StartSqlCommandExecute](4202-startsqlcommandexecute.md)|詳細資訊|開始 SQL 命令執行：%1|WFInstanceStore|  
|[4203 - RenewLockSystemError](4203-renewlocksystemerror.md)|Error|無法延長鎖定期限，已超過鎖定期限或已刪除鎖定擁有人。 正在中止 SqlWorkflowInstanceStore。|WFInstanceStore|  
|[4205 - FoundProcessingError](4205-foundprocessingerror.md)|Error|命令失敗：%1|WFInstanceStore|  
|[4206 - UnlockInstanceException](4206-unlockinstanceexception.md)|Error|嘗試解除鎖定執行個體時，發生例外狀況 %1。|WFInstanceStore|  
|[4207 - MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|內容|放棄重試 SQL 命令，因為已經執行了重試次數上限。|Quota WFInstanceStore|  
|[4208 - RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|內容|重試 SQL 命令，因為出現 SQL 錯誤代碼 %1。|WFInstanceStore|  
|[4209 - TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Error|嘗試開啟 SQL 連接時發生逾時。 無法在分配的逾時 %1 內完成作業。 分配給此作業的時間可能是較長逾時的一部分。|WFInstanceStore|  
|[4210 - SqlExceptionCaught](4210-sqlexceptioncaught.md)|警告|攔截到 SQL 例外狀況編號 %1 訊息 %2。|WFInstanceStore|  
|[4211 - QueuingSqlRetry](4211-queuingsqlretry.md)|警告|佇列 SQL 重試，但延遲 %1 毫秒。|WFInstanceStore|  
|[4212 - LockRetryTimeout](4212-lockretrytimeout.md)|警告|嘗試取得實例鎖定的超時時間。  無法在分配的逾時 %1 內完成作業。 分配給此作業的時間可能是較長逾時的一部分。|WFInstanceStore|  
|[4213 - RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Error|偵測可執行的執行個體失敗，因為發生下列例外狀況|WFInstanceStore|  
|[4214 - InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Error|復原執行個體鎖定失敗，因為發生下列例外狀況|WFInstanceStore|  
|[39456 - TrackingRecordDropped](39456-trackingrecorddropped.md)|警告|追蹤記錄 %1 的大小已超出提供者 %2 的 ETW 工作階段所允許的最大值|WFTracking|  
|[39457 - TrackingRecordRaised](39457-trackingrecordraised.md)|內容|追蹤記錄 %1 提升至 %2。|WFRuntime|  
|[39458 - TrackingRecordTruncated](39458-trackingrecordtruncated.md)|警告|已將截斷的追蹤記錄 %1 寫入提供者 %2 的 ETW 工作階段。 變數/附註/使用者資料已移除|WFTracking|  
|[39459 - TrackingDataExtracted](39459-trackingdataextracted.md)|詳細資訊|追蹤在活動 %2 中擷取到的資料 %1。|WFRuntime|  
|[39460 - TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|警告|擷取的引數/變數 '%1' 不可序列化。|WFTracking|  
|[57398 - MaxInstancesExceeded](57398-maxinstancesexceeded.md)|警告|系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。 此節流的限制設為 %1。 若要變更節流值，請修改 serviceThrottle 元素中的屬性 'maxConcurrentInstances'，或修改行為 ServiceThrottlingBehavior 的 'MaxConcurrentInstances' 屬性。|WFServices|
