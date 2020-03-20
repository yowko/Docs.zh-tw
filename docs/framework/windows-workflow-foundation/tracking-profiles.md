---
title: 追蹤設定檔
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9723b8fbb0bb8f24e8c9544d8bac8252b2fc763a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182732"
---
# <a name="tracking-profiles"></a>追蹤設定檔

追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。

## <a name="tracking-profiles"></a>追蹤設定檔

追蹤設定檔可用來指定要為工作流程執行個體發出哪些追蹤資訊。 如果未指定任何設定檔，則會發出所有追蹤事件。 如果有指定設定檔，則會發出設定檔中指定的追蹤事件。 根據您的監控需求，您可以寫入非常廣泛的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。 反之，您也可以建立非常詳細的設定檔，取得充分的結果事件，以便在日後重新建構為詳細的執行流程。

跟蹤設定檔在標準 .NET Framework 設定檔中或代碼中指定，以 XML 元素表示。 下列範例是組態檔中的 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 追蹤設定檔，可允許追蹤參與者訂閱 `Started` 和 `Completed` 工作流程事件。

```xml
<system.serviceModel>
    ...
    <tracking>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

下列範例顯示使用程式碼來建立的同等追蹤設定檔。

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

追蹤記錄是利用 <xref:System.Activities.Tracking.ImplementationVisibility> 屬性，透過追蹤設定檔內的可見性模式所篩選的。 複合活動是最上層的活動，其中包含構成其實作的其他活動。 可見性模式會透過指定從工作流程活動內的複合活動發出的追蹤記錄，指定是否要追蹤形成實作的活動。 可見性模式會在追蹤設定檔層級套用。 工作流程中個別活動的追蹤記錄篩選，是由追蹤設定檔中的查詢進行控制。 有關詳細資訊，請參閱本文檔中的 **"跟蹤設定檔查詢類型"** 部分。

追蹤設定檔中，以 `implementationVisibility` 屬性指定的兩個可見性模式為 `RootScope` 和 `All`。 若複合活動不是工作流程的根，使用 `RootScope` 模式會隱藏形成活動之實作的追蹤記錄。 也就是說，將使用其他活動實作的活動加入至工作流程中，且 `implementationVisibility` 設定為 RootScope 時，只會追蹤該複合活動內的最上層活動。 若活動是工作流程的根，則該活動的實作會是工作流程本身，且會針對形成實作的活動發出追蹤記錄。 使用 All 模式可發出根活動及所有其複合活動的全部追蹤記錄。

例如，假設*MyActivity*是一個複合活動，其實現包含兩個活動，*活動 1*和*活動 2*。 當此活動添加到工作流中，並且使用設置為`implementationVisibility`的跟蹤設定檔啟用跟蹤時`RootScope`，僅為*MyActivity*發出追蹤記錄。 但是，不會為*活動活動 1*和*活動 2*發出任何記錄。

但是，如果跟蹤`implementationVisibility`設定檔`All`的屬性設置為 ，則追蹤記錄不僅針對*MyActivity，* 而且還為*活動活動活動 1*和*Activity2*發出。

`implementationVisibility` 旗標適用於下列追蹤記錄類型：

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> implementationVisibility 設定不會篩選出從活動實作發出的 CustomTrackingRecords。

在下列程式碼中的追蹤設定檔中，會將 `implementationVisibility` 功能指定為 <xref:System.Activities.Tracking.ImplementationVisibility.RootScope>：

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

在下列組態檔的追蹤設定檔中，會將 `implementationVisibility` 功能指定為 <xref:System.Activities.Tracking.ImplementationVisibility.All>：

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

追蹤設定檔的 `ImplementationVisibility` 設定是選擇性的。 根據預設，其值會設定為 `RootScope`。 這個屬性的值也會區分大小寫。

### <a name="tracking-profile-query-types"></a>追蹤設定檔查詢類型

追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。 您可以使用數個查詢型別訂閱不同類別的 <xref:System.Activities.Tracking.TrackingRecord> 物件。 追蹤設定檔可在組態中指定，或是透過程式碼指定。 以下是最常見的查詢類型：

- <xref:System.Activities.Tracking.WorkflowInstanceQuery> - 使用這個查詢，即可追蹤工作流程執行個體生命週期變更，例如先前示範的 `Started` 和 `Completed`。 <xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  可供訂閱的狀態可於 <xref:System.Activities.Tracking.WorkflowInstanceStates> 類別中指定。

  下列範例示範使用 `Started` 訂閱 <xref:System.Activities.Tracking.WorkflowInstanceQuery> 執行個體狀態之工作流程執行個體層級追蹤記錄的組態或程式碼。

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.ActivityStateQuery> - 使用這個查詢，即可追蹤組成工作流程執行個體之活動的生命週期變更。 例如，您可能希望跟蹤工作流實例中每次完成"發送電子郵件"活動的時間。 <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.ActivityStateRecord> 物件時，必須要有這個查詢。 可供訂閱的狀態可於 <xref:System.Activities.Tracking.ActivityStates> 中指定。

  下列範例示範訂閱使用 <xref:System.Activities.Tracking.ActivityStateQuery> 做為 `SendEmailActivity` 活動之活動狀態追蹤記錄的組態和程式碼。

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > 如果多個 activityStateQuery 元素具有相同的名稱，追蹤設定檔只會使用最後一個元素中的狀態。

- <xref:System.Activities.Tracking.ActivityScheduledQuery> - 這個查詢可讓您追蹤由父活動排程執行的活動。 <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.ActivityScheduledRecord> 物件時，必須要有這個查詢。

  下列範例示範訂閱使用 `SendEmailActivity` 排定的 <xref:System.Activities.Tracking.ActivityScheduledQuery> 子活動之相關記錄的組態和程式碼。

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.FaultPropagationQuery> - 使用這個查詢，即可追蹤活動中發生的錯誤處理。 <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.FaultPropagationRecord> 物件時，必須要有這個查詢。

  下列範例示範使用 <xref:System.Activities.Tracking.FaultPropagationQuery> 訂閱與錯誤傳播相關之記錄的組態和程式碼。

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CancelRequestedQuery> - 使用這個查詢，即可追蹤父活動取消子活動的要求。 <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.CancelRequestedRecord> 物件時，必須要有這個查詢。

  用於訂閱與使用<xref:System.Activities.Tracking.CancelRequestedQuery>的活動取消相關的記錄的配置和代碼顯示在以下示例中。

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CustomTrackingQuery>- 使用這個查詢，即可追蹤程式碼活動中定義的事件。 <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.CustomTrackingRecord> 物件時，必須要有這個查詢。

  下列範例示範使用 <xref:System.Activities.Tracking.CustomTrackingQuery> 訂閱與自訂追蹤記錄相關之記錄的組態和程式碼。

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.BookmarkResumptionQuery> - 使用這個查詢，即可追蹤工作流程執行個體中書籤的繼續。 <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.BookmarkResumptionRecord> 物件時，必須要有這個查詢。

  下列範例示範使用 <xref:System.Activities.Tracking.BookmarkResumptionQuery> 訂閱與書籤繼續相關之記錄的組態和程式碼。

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a>註解

附註可讓您使用值任意標記追蹤記錄，該值可在建置階段後設定。 例如，您可能希望使用"郵件伺服器"="郵件伺服器1"標記多個工作流中的多個追蹤記錄。 當您稍後查詢追蹤記錄時，就可以更輕鬆地找到所有具有這個標記的記錄。

若要完成這個目的，就需要將附註加入至追蹤查詢，如下列範例所示。

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a>如何建立追蹤設定檔

跟蹤查詢元素用於使用 XML 設定檔或[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]代碼創建跟蹤設定檔。 以下是使用組態檔建立的追蹤設定檔範例。

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> 針對使用工作流程服務主機的 WF，追蹤設定檔通常會使用組態檔建立。 您也可以使用追蹤設定檔和追蹤查詢 API，以程式碼建立追蹤設定檔。

設定為 XML 組態檔的設定檔會使用行為擴充套用至追蹤參與者。 這將添加到工作流服務主機中，如後面的"[配置工作流跟蹤"中](configuring-tracking-for-a-workflow.md)所述。

主機發出之追蹤記錄的詳細資訊取決於追蹤設定檔內的組態設定。 追蹤參與者可將查詢加入至追蹤設定檔，以訂閱追蹤記錄。 要訂閱所有追蹤記錄，跟蹤設定檔需要在每個查詢的名稱欄位中使用""\*指定所有跟蹤查詢。

以下是追蹤設定檔的一些通用範例。

- 取得工作流程執行個體記錄和錯誤的追蹤設定檔。

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- 取得所有自訂追蹤記錄的追蹤設定檔。

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a>另請參閱

- [SQL 追蹤](./samples/sql-tracking.md)
- [Windows 伺服器應用結構監視](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [使用應用交換矩陣監視應用程式](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
