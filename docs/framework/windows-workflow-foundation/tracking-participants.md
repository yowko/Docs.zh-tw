---
title: 追蹤參與者
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 6c42712300baa6d7e12b9a29d94c925caaad5141
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340174"
---
# <a name="tracking-participants"></a><span data-ttu-id="b3887-102">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="b3887-102">Tracking Participants</span></span>
<span data-ttu-id="b3887-103">追蹤參與者是可讓工作流程開發人員存取 <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> 物件並加以處理的擴充點。</span><span class="sxs-lookup"><span data-stu-id="b3887-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="b3887-104">包含寫入追蹤記錄以做為 Windows 事件追蹤 (ETW) 事件的標準追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="b3887-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="b3887-105">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="b3887-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="b3887-106">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="b3887-106">Tracking Participants</span></span>  
 <span data-ttu-id="b3887-107">追蹤基礎結構可讓應用程式篩選外送的追蹤記錄，讓參與者可訂閱記錄的子集。</span><span class="sxs-lookup"><span data-stu-id="b3887-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="b3887-108">此機制會透過追蹤設定檔來套用篩選。</span><span class="sxs-lookup"><span data-stu-id="b3887-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="b3887-109">Windows Workflow Foundation (WF) 中[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]提供將追蹤記錄寫入至 ETW 工作階段的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="b3887-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b3887-110">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="b3887-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="b3887-111">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b3887-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="b3887-112">ETW 式追蹤的 SDK 範例是熟悉使用 ETW 式追蹤參與者之 WF 追蹤的理想方式。</span><span class="sxs-lookup"><span data-stu-id="b3887-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="b3887-113">ETW 追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="b3887-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="b3887-114">包含將追蹤記錄寫入至 ETW 工作階段的 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="b3887-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b3887-115">這是非常有效率的方式，對應用程式效能或伺服器輸送量所造成的衝擊最小。</span><span class="sxs-lookup"><span data-stu-id="b3887-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="b3887-116">使用標準 ETW 追蹤參與者的優點在於，可在 Windows 事件檢視器中使用其他應用程式和系統記錄來檢視它所收到的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b3887-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="b3887-117">標準 ETW 追蹤參與者會在 Web.config 檔中配置，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="b3887-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="b3887-118">如果未指定 `trackingProfile` 名稱，例如只有 `<etwTracking/>` 或 `<etwTracking profileName=""/>`，則會使用 Machine.config 檔中連同 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安裝的預設追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="b3887-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="b3887-119">在 Machine.config 檔中，預設追蹤設定檔會訂閱工作流程執行個體記錄和錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3887-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="b3887-120">在 ETW 中，會透過提供者 ID 將事件寫入 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b3887-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="b3887-121">ETW 追蹤參與者用來將追蹤記錄寫入至 ETW 的提供者 ID，是定義於 Web.config 檔中的診斷工作階段 (在 `<system.serviceModel><diagnostics>` 下)。</span><span class="sxs-lookup"><span data-stu-id="b3887-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="b3887-122">根據預設，當未指定提供者 ID 時，ETW 追蹤參與者會使用預設提供者 ID，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="b3887-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="b3887-123">下圖顯示透過 ETW 追蹤參與者追蹤資料的流程。</span><span class="sxs-lookup"><span data-stu-id="b3887-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="b3887-124">一旦追蹤資料到達 ETW 工作階段，就可以透過多種方式加以存取。</span><span class="sxs-lookup"><span data-stu-id="b3887-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="b3887-125">其中最實用的方式之一就是透過事件檢視器，這是常用的 Windows 工具，可用來檢視記錄並從應用程式和服務進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b3887-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![追蹤 ETW 追蹤提供者所提供的資料的流程。](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="b3887-127">追蹤參與者事件資料</span><span class="sxs-lookup"><span data-stu-id="b3887-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="b3887-128">追蹤參與者會以每個追蹤記錄包含一個事件的形式，將已追蹤的事件資料序列化至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b3887-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="b3887-129">事件會使用從 100 到 199 範圍的 ID 來識別。</span><span class="sxs-lookup"><span data-stu-id="b3887-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="b3887-130">如需追蹤事件的定義記錄發出的追蹤參與者，請參閱[追蹤事件參考](tracking-events-reference.md)主題。</span><span class="sxs-lookup"><span data-stu-id="b3887-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="b3887-131">ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制，兩者的值都較小。</span><span class="sxs-lookup"><span data-stu-id="b3887-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="b3887-132">如果事件大小超過這裡任一種 ETW 限制，則會截斷事件，並任意移除其內容。</span><span class="sxs-lookup"><span data-stu-id="b3887-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="b3887-133">變數、引數、附註和自訂資料都不可選擇性移除。</span><span class="sxs-lookup"><span data-stu-id="b3887-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="b3887-134">發生截斷情形時，不論造成事件大小超出 ETW 限制的值大小為何，這些元素全都會遭到截斷。</span><span class="sxs-lookup"><span data-stu-id="b3887-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="b3887-135">已移除的資料會以 `<item>..<item>` 來取代。</span><span class="sxs-lookup"><span data-stu-id="b3887-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="b3887-136">複雜型別變數、 引數，和自訂資料項目會序列化至 ETW 記錄使用事件[NetDataContractSerializer 類別](https://go.microsoft.com/fwlink/?LinkId=177537)。</span><span class="sxs-lookup"><span data-stu-id="b3887-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](https://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="b3887-137">此類別包含序列化 XML 資料流中的 CLR 型別資訊。</span><span class="sxs-lookup"><span data-stu-id="b3887-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="b3887-138">因 ETW 限制而截斷承載資料，可能會造成將追蹤記錄傳送到 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b3887-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="b3887-139">如果有一個以上的工作階段正在接聽事件，且工作階段有不同的事件承載限制時，就可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="b3887-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="b3887-140">至於限制較低的工作階段可能會截斷事件。</span><span class="sxs-lookup"><span data-stu-id="b3887-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="b3887-141">ETW 追蹤參與者並不知道工作階段接聽事件的數量；如果在工作階段中某個事件遭到截斷，則 ETW 參與者就會再試著傳送事件一次。</span><span class="sxs-lookup"><span data-stu-id="b3887-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="b3887-142">在這樣的情況下，將工作階段配置為接受較大承載大小，就會收到事件兩次 (未遭到截斷與遭到截斷的事件)。</span><span class="sxs-lookup"><span data-stu-id="b3887-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="b3887-143">將所有 ETW 工作階段配置為相同的緩衝區大小限制，即可避免發生重複。</span><span class="sxs-lookup"><span data-stu-id="b3887-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="b3887-144">在事件檢視器中從 ETW 追蹤參與者存取追蹤記錄資料</span><span class="sxs-lookup"><span data-stu-id="b3887-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="b3887-145">由 ETW 追蹤參與者寫入至 ETW 工作階段的事件，可透過事件檢視器進行存取 (當使用預設提供者 ID 時)。</span><span class="sxs-lookup"><span data-stu-id="b3887-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="b3887-146">這可快速檢視已由工作流程發出的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b3887-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3887-147">發出至 ETW 工作階段的追蹤記錄事件會使用從 100 到 199 範圍的事件 ID。</span><span class="sxs-lookup"><span data-stu-id="b3887-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="b3887-148">若要在事件檢視器中檢視追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="b3887-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="b3887-149">啟動事件檢視器 (EVENTVWR.EXE)</span><span class="sxs-lookup"><span data-stu-id="b3887-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="b3887-150">選取 **事件檢視器、 應用程式和服務記錄檔、 Microsoft、 Windows、 應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="b3887-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="b3887-151">以滑鼠右鍵按一下，並確定**檢視、 顯示分析與偵錯記錄檔**已選取。</span><span class="sxs-lookup"><span data-stu-id="b3887-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="b3887-152">如果未選取該選項，請加以選取，使其旁邊出現核取記號。</span><span class="sxs-lookup"><span data-stu-id="b3887-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="b3887-153">這會顯示**分析**，**效能**，並**偵錯**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b3887-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="b3887-154">以滑鼠右鍵按一下**分析**記錄，然後選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="b3887-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="b3887-155">記錄檔將位於 %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3887-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="b3887-156">自訂追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="b3887-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="b3887-157">追蹤參與者 API 允許以使用者提供的追蹤者來擴充追蹤執行階段，可包含自訂邏輯以處理工作流程執行階段發出的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b3887-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="b3887-158">若要寫入自訂追蹤參與者，開發人員必須實作 `Track` 類別上的 <xref:System.Activities.Tracking.TrackingParticipant> 方法。</span><span class="sxs-lookup"><span data-stu-id="b3887-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="b3887-159">當工作流程執行階段發出追蹤記錄時，會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b3887-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="b3887-160">追蹤參與者衍生自 <xref:System.Activities.Tracking.TrackingParticipant> 類別。</span><span class="sxs-lookup"><span data-stu-id="b3887-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="b3887-161">系統提供的 <xref:System.Activities.Tracking.EtwTrackingParticipant> 會針對所收到的每個追蹤記錄發出 Windows 事件追蹤 (ETW) 事件。</span><span class="sxs-lookup"><span data-stu-id="b3887-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="b3887-162">若要建立自訂追蹤參與者，會建立衍生自 <xref:System.Activities.Tracking.TrackingParticipant> 的類別。</span><span class="sxs-lookup"><span data-stu-id="b3887-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="b3887-163">若要提供基本追蹤功能，請覆寫 <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>。</span><span class="sxs-lookup"><span data-stu-id="b3887-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="b3887-164">當執行階段傳送追蹤記錄且可以想要的方式來處理時，就會呼叫 <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>。</span><span class="sxs-lookup"><span data-stu-id="b3887-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="b3887-165">在以下範例中，自訂追蹤參與者的類別是定義為發出所有追蹤記錄至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="b3887-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="b3887-166">您也可實作 <xref:System.Activities.Tracking.TrackingParticipant> 物件，此物件會使用其 `BeginTrack` 和 `EndTrack` 方法來非同步處理追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b3887-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b3887-167">若要使用特定追蹤參與者，請使用您想追蹤的工作流程執行個體來進行登錄，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="b3887-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="b3887-168">在以下範例中，會建立由 <xref:System.Activities.Statements.Sequence> 活動構成的工作流程，此工作流程包含 <xref:System.Activities.Statements.WriteLine> 活動。</span><span class="sxs-lookup"><span data-stu-id="b3887-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="b3887-169">`ConsoleTrackingParticipant` 會加入擴充，並叫用工作流程。</span><span class="sxs-lookup"><span data-stu-id="b3887-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3887-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3887-170">See also</span></span>

- [<span data-ttu-id="b3887-171">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="b3887-171">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="b3887-172">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="b3887-172">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
