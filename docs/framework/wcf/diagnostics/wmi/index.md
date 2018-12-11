---
title: 使用 Windows Management Instrumentation 進行診斷
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: a5dae1479c9be7954b9eec1eed197f358eb48e4f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239510"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="50ab6-102">使用 Windows Management Instrumentation 進行診斷</span><span class="sxs-lookup"><span data-stu-id="50ab6-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="50ab6-103">Windows Communication Foundation (WCF) 公開服務，以在透過 WCF Windows Management Instrumentation (WMI) 提供者的執行階段檢查的資料。</span><span class="sxs-lookup"><span data-stu-id="50ab6-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="50ab6-104">啟用 WMI</span><span class="sxs-lookup"><span data-stu-id="50ab6-104">Enabling WMI</span></span>  
 <span data-ttu-id="50ab6-105">WMI 是 Microsoft 對「Web 架構企業管理」(Web-Based Enterprise Management，WBEM) 標準的實作。</span><span class="sxs-lookup"><span data-stu-id="50ab6-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="50ab6-106">如需有關 WMI SDK 的詳細資訊，請參閱 < [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page)。</span><span class="sxs-lookup"><span data-stu-id="50ab6-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="50ab6-107">WBEM 是一套業界標準，說明應用程式如何將管理測試設備公開至外部管理工具。</span><span class="sxs-lookup"><span data-stu-id="50ab6-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="50ab6-108">WMI 提供者是一個元件，可透過 WBEM 相容介面，在執行階段公開測試設備。</span><span class="sxs-lookup"><span data-stu-id="50ab6-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="50ab6-109">它是由一組含有屬性/值配對的 WMI 物件所組成。</span><span class="sxs-lookup"><span data-stu-id="50ab6-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="50ab6-110">配對可以是數個簡單型別。</span><span class="sxs-lookup"><span data-stu-id="50ab6-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="50ab6-111">管理工具可以在執行階段，透過介面連接到服務。</span><span class="sxs-lookup"><span data-stu-id="50ab6-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="50ab6-112">WCF 會公開服務，例如位址、 繫結、 行為和接聽程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="50ab6-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="50ab6-113">內建的 WMI 提供者可以在應用程式的組態檔中啟動。</span><span class="sxs-lookup"><span data-stu-id="50ab6-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="50ab6-114">這是透過`wmiProviderEnabled`的屬性[\<診斷 >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)中[ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)區段，如下列範例所示組態設定。</span><span class="sxs-lookup"><span data-stu-id="50ab6-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="50ab6-115">這個組態項目會公開 WMI 介面。</span><span class="sxs-lookup"><span data-stu-id="50ab6-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="50ab6-116">現在，管理應用程式可以透過這個介面進行連線，並存取應用程式的管理測試設備。</span><span class="sxs-lookup"><span data-stu-id="50ab6-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="50ab6-117">存取 WMI 資料</span><span class="sxs-lookup"><span data-stu-id="50ab6-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="50ab6-118">您可以使用各種不同的方式來存取 WMI 資料。</span><span class="sxs-lookup"><span data-stu-id="50ab6-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="50ab6-119">Microsoft 指令碼、 Visual Basic 應用程式、 c + + 應用程式，提供了 WMI Api 和[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="50ab6-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="50ab6-120">如需詳細資訊，請參閱 <<c0> [ 使用 WMI](https://go.microsoft.com/fwlink/?LinkId=95183)。</span><span class="sxs-lookup"><span data-stu-id="50ab6-120">For more information, see [Using WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="50ab6-121">如果您使用 .NET Framework 提供的方法，以程式設計方式存取 WMI 資料，您要注意，當連線建立時，這類方法可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50ab6-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="50ab6-122">連線不是在建構 <xref:System.Management.ManagementObject> 執行個體期間建立的，而是在第一次要求實際資料交換時建立。</span><span class="sxs-lookup"><span data-stu-id="50ab6-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="50ab6-123">因此，您應該使用 `try..catch` 區塊攔截可能的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50ab6-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="50ab6-124">您可以在 WMI 中變更 `System.ServiceModel` 追蹤來源的追蹤和訊息記錄層級，以及訊息記錄選項。</span><span class="sxs-lookup"><span data-stu-id="50ab6-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="50ab6-125">這可以藉由存取[AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)執行個體，它會公開下列布林值屬性： `LogMessagesAtServiceLevel`， `LogMessagesAtTransportLevel`， `LogMalformedMessages`，和`TraceLevel`。</span><span class="sxs-lookup"><span data-stu-id="50ab6-125">This can be done by accessing the [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="50ab6-126">因此，如果您為訊息記錄設定一個追蹤接聽項，但在組態中將這些選項設定為 `false`，那麼您可以在稍後應用程式執行時，將選項變更為 `true`。</span><span class="sxs-lookup"><span data-stu-id="50ab6-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="50ab6-127">這將會在執行階段有效地啟用訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="50ab6-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="50ab6-128">同樣地，如果您在組態檔中啟用訊息記錄，則您可以在執行階段使用 WMI 來停用訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="50ab6-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="50ab6-129">您要注意，如果沒有為訊息記錄設定訊息記錄追蹤接聽項，或者組態檔中沒有指定 `System.ServiceModel` 追蹤接聽項來進行追蹤，則您所做的變更不會有任何作用，即使 WMI 接受這些變更也一樣。</span><span class="sxs-lookup"><span data-stu-id="50ab6-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="50ab6-130">如需正確設定各接聽項的詳細資訊，請參閱[設定訊息記錄](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)並[設定追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="50ab6-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) and [Configuring Tracing](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="50ab6-131">組態所指定之所有其他追蹤來源的追蹤層級，會在應用程式啟動時生效，並且無法變更。</span><span class="sxs-lookup"><span data-stu-id="50ab6-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="50ab6-132">WCF 會公開`GetOperationCounterInstanceName`指令碼處理方法。</span><span class="sxs-lookup"><span data-stu-id="50ab6-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="50ab6-133">如果您提供了一個作業名稱，這個方法就會傳回一個效能計數器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="50ab6-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="50ab6-134">不過，它不會驗證您的輸入。</span><span class="sxs-lookup"><span data-stu-id="50ab6-134">However, it does not validate your input.</span></span> <span data-ttu-id="50ab6-135">因此，如果您提供的作業名稱不正確，就會傳回錯誤的計數器名稱。</span><span class="sxs-lookup"><span data-stu-id="50ab6-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="50ab6-136">`OutgoingChannel`的屬性`Service`執行個體不會計算內未建立至目的地服務的 WCF 用戶端連線到另一個服務，服務所開啟的通道`Service`方法。</span><span class="sxs-lookup"><span data-stu-id="50ab6-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="50ab6-137">**請小心**WMI 只支援<xref:System.TimeSpan>值最多 3 個小數位數。</span><span class="sxs-lookup"><span data-stu-id="50ab6-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="50ab6-138">例如，如果您的服務將其中一個屬性設定為 <xref:System.TimeSpan.MaxValue>，則透過 WMI 檢視時，小數點後三位之後的值將被截斷。</span><span class="sxs-lookup"><span data-stu-id="50ab6-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="50ab6-139">安全性</span><span class="sxs-lookup"><span data-stu-id="50ab6-139">Security</span></span>  
 <span data-ttu-id="50ab6-140">因為 WCF WMI 提供者允許在環境中的探索服務，所以您應該特別小心謹慎授與存取權。</span><span class="sxs-lookup"><span data-stu-id="50ab6-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="50ab6-141">如果您將預設僅供系統管理員存取的限制放寬，可能導致信賴度較低的一方存取環境中的敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="50ab6-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="50ab6-142">特別是，如果您放寬遠端 WMI 存取的權限，可能導致氾濫攻擊。</span><span class="sxs-lookup"><span data-stu-id="50ab6-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="50ab6-143">如果某個處理序湧入了大量 WMI 要求，可能會使它的效能降低。</span><span class="sxs-lookup"><span data-stu-id="50ab6-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="50ab6-144">此外，如果您放寬了 MOF 檔案的存取權限，信賴度較低的一方就可以操控 WMI 的行為，並改變 WMI 結構描述中載入的物件。</span><span class="sxs-lookup"><span data-stu-id="50ab6-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="50ab6-145">例如，欄位可能會遭到移除，導致管理員無法看見重要資料，或是原本不會填入或造成例外狀況的欄位會加入至檔案。</span><span class="sxs-lookup"><span data-stu-id="50ab6-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="50ab6-146">根據預設，WCF WMI 提供者授與 「 執行方法 」、 「 提供者寫入 」 和 「 啟用帳戶 」 為系統管理員的權限，以及 ASP.NET、 本機服務和網路服務的 「 啟用帳戶 」 權限。</span><span class="sxs-lookup"><span data-stu-id="50ab6-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="50ab6-147">特別是，在非 [!INCLUDE[wv](../../../../../includes/wv-md.md)] 平台上，ASP.NET 帳戶具有 WMI ServiceModel 命名空間的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="50ab6-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="50ab6-148">如果您不想將這些權限授與特定使用者群組，則應該停用 WMI 提供者 (預設為停用) 或停用特定使用者群組的存取。</span><span class="sxs-lookup"><span data-stu-id="50ab6-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="50ab6-149">此外，當您嘗試透過組態啟用 WMI 時，可能因為使用者權限不足，而無法啟用 WMI。</span><span class="sxs-lookup"><span data-stu-id="50ab6-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="50ab6-150">不過，事件記錄內不會寫入任何事件以記錄這項失敗。</span><span class="sxs-lookup"><span data-stu-id="50ab6-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="50ab6-151">若要修改使用者權限層級，請依照下列步驟執行。</span><span class="sxs-lookup"><span data-stu-id="50ab6-151">To modify user privilege levels, use the following steps.</span></span>  
  
1.  <span data-ttu-id="50ab6-152">按一下 [開始]，然後執行，並輸入**compmgmt.msc**。</span><span class="sxs-lookup"><span data-stu-id="50ab6-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2.  <span data-ttu-id="50ab6-153">以滑鼠右鍵按一下**服務和應用程式 /WMI 控制項**來選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="50ab6-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3.  <span data-ttu-id="50ab6-154">選取 **安全性**索引標籤上，並瀏覽至**Root/ServiceModel**命名空間。</span><span class="sxs-lookup"><span data-stu-id="50ab6-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="50ab6-155">按一下 [**安全性**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="50ab6-155">Click the **Security** button.</span></span>  
  
4.  <span data-ttu-id="50ab6-156">選取 特定群組或您想要控制存取和使用的使用者**允許**或是**拒絕**核取方塊以設定權限。</span><span class="sxs-lookup"><span data-stu-id="50ab6-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="50ab6-157">將 WCF WMI 註冊權限授與其他使用者</span><span class="sxs-lookup"><span data-stu-id="50ab6-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="50ab6-158">WCF 會將管理資料公開至 WMI。</span><span class="sxs-lookup"><span data-stu-id="50ab6-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="50ab6-159">它會裝載同處理序 WMI 提供者，有時也稱為 「 低耦合提供者 」。</span><span class="sxs-lookup"><span data-stu-id="50ab6-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="50ab6-160">若要讓管理資料公開，註冊此提供者的帳戶必須有適當權限。</span><span class="sxs-lookup"><span data-stu-id="50ab6-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="50ab6-161">在 Windows 中，預設只有一小組授權的帳戶可以登錄低耦合提供者。</span><span class="sxs-lookup"><span data-stu-id="50ab6-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="50ab6-162">這是一個問題，因為使用者通常想要從非預設集合中之帳戶下執行的 WCF 服務公開 WMI 資料。</span><span class="sxs-lookup"><span data-stu-id="50ab6-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="50ab6-163">若要提供此存取權，系統管理員必須依下列順序將下列權限授與其他帳戶：</span><span class="sxs-lookup"><span data-stu-id="50ab6-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1.  <span data-ttu-id="50ab6-164">存取 WCF WMI 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="50ab6-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2.  <span data-ttu-id="50ab6-165">註冊 WCF 低耦合 WMI 提供者的權限。</span><span class="sxs-lookup"><span data-stu-id="50ab6-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="50ab6-166">若要授與 WMI 命名空間存取權限</span><span class="sxs-lookup"><span data-stu-id="50ab6-166">To grant WMI namespace access permission</span></span>  
  
1.  <span data-ttu-id="50ab6-167">執行下列 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="50ab6-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="50ab6-168">此 PowerShell 指令碼使用 Security Descriptor Definition Language (SDDL) 授與內建的使用者群組存取"root/servicemodel"WMI 命名空間。</span><span class="sxs-lookup"><span data-stu-id="50ab6-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="50ab6-169">它指定下列 ACL：</span><span class="sxs-lookup"><span data-stu-id="50ab6-169">It specifies the following ACLs:</span></span>  
  
    -   <span data-ttu-id="50ab6-170">內建系統管理員 (BA) - 已經有存取權。</span><span class="sxs-lookup"><span data-stu-id="50ab6-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="50ab6-171">網路服務 (NS) - 已經有存取權。</span><span class="sxs-lookup"><span data-stu-id="50ab6-171">Network Service (NS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="50ab6-172">本機系統 (LS) - 已經有存取權。</span><span class="sxs-lookup"><span data-stu-id="50ab6-172">Local System (LS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="50ab6-173">內建使用者 - 要授與存取權的目標群組。</span><span class="sxs-lookup"><span data-stu-id="50ab6-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="50ab6-174">若要授與提供者註冊存取</span><span class="sxs-lookup"><span data-stu-id="50ab6-174">To grant provider registration access</span></span>  
  
1.  <span data-ttu-id="50ab6-175">執行下列 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="50ab6-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="50ab6-176">授與任意使用者或群組存取權</span><span class="sxs-lookup"><span data-stu-id="50ab6-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="50ab6-177">本節中的範例會將 WMI 提供者註冊權限授與所有本機使用者。</span><span class="sxs-lookup"><span data-stu-id="50ab6-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="50ab6-178">如果您要授與非內建使用者或群組存取權，必須取得該使用者或群組的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="50ab6-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="50ab6-179">目前沒有簡易的方法可以取得任意使用者的 SID。</span><span class="sxs-lookup"><span data-stu-id="50ab6-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="50ab6-180">一個方法是以所要的使用者身分登入，然後發出下列 Shell 命令。</span><span class="sxs-lookup"><span data-stu-id="50ab6-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```  
Whoami /user  
```  
  
 <span data-ttu-id="50ab6-181">這個方法會提供目前使用者的 SID，但無法用來取得任意使用者的 SID。</span><span class="sxs-lookup"><span data-stu-id="50ab6-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="50ab6-182">另一個取得 SID，方法是使用[getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467)工具[Windows 2000 Resource Kit 工具用於系統管理工作](https://go.microsoft.com/fwlink/?LinkId=178660)。</span><span class="sxs-lookup"><span data-stu-id="50ab6-182">Another method to get the SID is to use the [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](https://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="50ab6-183">此工具會比較兩個使用者 (本機或網域) 的 SID，並以副作用方式將兩個 SID 列印至命令列。</span><span class="sxs-lookup"><span data-stu-id="50ab6-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="50ab6-184">如需詳細資訊，請參閱 <<c0> [ 已知 Sid](https://go.microsoft.com/fwlink/?LinkId=186468)。</span><span class="sxs-lookup"><span data-stu-id="50ab6-184">For more information, see [Well Known SIDs](https://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="50ab6-185">存取遠端 WMI 物件執行個體</span><span class="sxs-lookup"><span data-stu-id="50ab6-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="50ab6-186">如果您需要存取 WCF WMI 執行個體，在遠端電腦上的，您必須啟用您用來存取的工具上的封包私密性。</span><span class="sxs-lookup"><span data-stu-id="50ab6-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="50ab6-187">下列小節說明如何使用 WMI CIM Studio、Windows Management Instrumentation 測試器以及 .NET SDK 2.0 來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="50ab6-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="50ab6-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="50ab6-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="50ab6-189">如果您已安裝[WMI 系統管理工具](https://go.microsoft.com/fwlink/?LinkId=95185)，您可以使用 WMI CIM Studio 來存取 WMI 執行個體。</span><span class="sxs-lookup"><span data-stu-id="50ab6-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="50ab6-190">工具位於下列資料夾中</span><span class="sxs-lookup"><span data-stu-id="50ab6-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="50ab6-191">**%windir%\Program Files\WMI 工具\\**</span><span class="sxs-lookup"><span data-stu-id="50ab6-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1.  <span data-ttu-id="50ab6-192">在 **連接至命名空間：** 視窗中，輸入**root\ServiceModel**按一下**確定。**</span><span class="sxs-lookup"><span data-stu-id="50ab6-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2.  <span data-ttu-id="50ab6-193">在 [ **WMI CIM Studio 登入**] 視窗中，按一下**選項 >>** 按鈕展開視窗。</span><span class="sxs-lookup"><span data-stu-id="50ab6-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="50ab6-194">選取**封包私密性**for**驗證層級**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="50ab6-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="50ab6-195">Windows Management Instrumentation 測試器</span><span class="sxs-lookup"><span data-stu-id="50ab6-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="50ab6-196">這個工具是由 Windows 進行安裝。</span><span class="sxs-lookup"><span data-stu-id="50ab6-196">This tool is installed by Windows.</span></span> <span data-ttu-id="50ab6-197">若要執行它，請啟動命令主控台中輸入**cmd.exe**中**開始/執行**對話方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="50ab6-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="50ab6-198">然後，輸入**wbemtest.exe**命令視窗中。</span><span class="sxs-lookup"><span data-stu-id="50ab6-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="50ab6-199">[Windows Management Instrumentation 測試器] 工具隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="50ab6-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1.  <span data-ttu-id="50ab6-200">按一下  **Connect**視窗的右上角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="50ab6-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2.  <span data-ttu-id="50ab6-201">在新視窗中，輸入**root\ServiceModel** for**命名空間**欄位，然後選取**封包私密性**如**驗證層級**。</span><span class="sxs-lookup"><span data-stu-id="50ab6-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="50ab6-202">按一下 **[Connect]**(連線)。</span><span class="sxs-lookup"><span data-stu-id="50ab6-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="50ab6-203">使用 Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="50ab6-203">Using Managed Code</span></span>  
 <span data-ttu-id="50ab6-204">您也可以使用 <xref:System.Management> 命名空間提供的類別，以程式設計方式存取遠端 WMI 執行個體。</span><span class="sxs-lookup"><span data-stu-id="50ab6-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="50ab6-205">下列程式碼範例示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="50ab6-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
