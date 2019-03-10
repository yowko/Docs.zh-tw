---
title: 追蹤設定檔
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 2fa4d65a6f0056824b2fc9dd67b93608777fc75d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721368"
---
# <a name="tracking-profiles"></a>追蹤設定檔

追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。

## <a name="tracking-profiles"></a>追蹤設定檔

追蹤設定檔可用來指定要為工作流程執行個體發出哪些追蹤資訊。 如果未指定任何設定檔，則會發出所有追蹤事件。 如果有指定設定檔，則會發出設定檔中指定的追蹤事件。 根據您的監控需求，您可以寫入非常廣泛的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。 反之，您也可以建立非常詳細的設定檔，取得充分的結果事件，以便在日後重新建構為詳細的執行流程。

追蹤設定檔會顯示為標準 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組態檔中的 XML 項目，或在程式碼中指定。 下列範例是組態檔中的 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 追蹤設定檔，可允許追蹤參與者訂閱 `Started` 和 `Completed` 工作流程事件。

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

追蹤記錄是利用 <xref:System.Activities.Tracking.ImplementationVisibility> 屬性，透過追蹤設定檔內的可見性模式所篩選的。 複合活動是最上層的活動，其中包含構成其實作的其他活動。 可見性模式會透過指定從工作流程活動內的複合活動發出的追蹤記錄，指定是否要追蹤形成實作的活動。 可見性模式會在追蹤設定檔層級套用。 工作流程中個別活動的追蹤記錄篩選，是由追蹤設定檔中的查詢進行控制。 如需詳細資訊，請參閱 <<c0>  **追蹤設定檔查詢類型**這份文件中的一節。

追蹤設定檔中，以 `implementationVisibility` 屬性指定的兩個可見性模式為 `RootScope` 和 `All`。 若複合活動不是工作流程的根，使用 `RootScope` 模式會隱藏形成活動之實作的追蹤記錄。 也就是說，將使用其他活動實作的活動加入至工作流程中，且 `implementationVisibility` 設定為 RootScope 時，只會追蹤該複合活動內的最上層活動。 若活動是工作流程的根，則該活動的實作會是工作流程本身，且會針對形成實作的活動發出追蹤記錄。 使用 All 模式可發出根活動及所有其複合活動的全部追蹤記錄。

例如，假設*MyActivity*其實作包含兩個活動，是複合活動*Activity1*並*Activity2*。 當這個活動加入至工作流程，並追蹤已啟用的追蹤設定檔`implementationVisibility`設定為`RootScope`，追蹤記錄只會發出*MyActivity*。 不過，活動會發出任何記錄*Activity1*並*Activity2*。

不過，如果`implementationVisibility`屬性 (attribute) 的追蹤設定檔設定為`All`，則不只發出追蹤記錄*MyActivity*，，而且還可活動*Activity1*並*Activity2*。


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

- <xref:System.Activities.Tracking.ActivityStateQuery> - 使用這個查詢，即可追蹤組成工作流程執行個體之活動的生命週期變更。 例如，您可能要追蹤的每次在 「 傳送電子郵件 」 活動完成的工作流程執行個體內。 
  <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.ActivityStateRecord> 物件時，必須要有這個查詢。 可供訂閱的狀態可於 <xref:System.Activities.Tracking.ActivityStates> 中指定。

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

- <xref:System.Activities.Tracking.CancelRequestedQuery> - 使用這個查詢，即可追蹤父活動取消子活動的要求。 
  <xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.CancelRequestedRecord> 物件時，必須要有這個查詢。

    用來訂閱記錄的程式碼與組態相關活動取消使用<xref:System.Activities.Tracking.CancelRequestedQuery>下列範例所示。

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

### <a name="annotations"></a>標註

附註可讓您使用值任意標記追蹤記錄，該值可在建置階段後設定。 比方說，您可能會想數個追蹤記錄，跨多個工作流程，加上"Mail Server"= ="Mail Server1"。 當您稍後查詢追蹤記錄時，就可以更輕鬆地找到所有具有這個標記的記錄。

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

追蹤查詢元素可讓您使用 XML 組態檔或 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 程式碼來建立追蹤設定檔。 以下是使用組態檔建立的追蹤設定檔範例。

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

設定為 XML 組態檔的設定檔會使用行為擴充套用至追蹤參與者。 這加入至 WorkflowServiceHost，如稍後章節所述[設定工作流程追蹤](configuring-tracking-for-a-workflow.md)。

主機發出之追蹤記錄的詳細資訊取決於追蹤設定檔內的組態設定。 追蹤參與者可將查詢加入至追蹤設定檔，以訂閱追蹤記錄。 若要訂閱所有追蹤記錄，追蹤設定檔，必須先指定所有追蹤查詢，使用"\*」 在每個查詢中的 [名稱] 欄位中。

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

1. 取得所有自訂追蹤記錄的追蹤設定檔。

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
- [Windows Server App Fabric 監控](https://go.microsoft.com/fwlink/?LinkId=201273)
- [使用 App Fabric 監控應用程式](https://go.microsoft.com/fwlink/?LinkId=201275)
