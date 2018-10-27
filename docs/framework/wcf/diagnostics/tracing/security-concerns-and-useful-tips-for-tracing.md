---
title: 追蹤的安全性考量及實用秘訣
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 439484cf5df6311bef56be0e28e5949c79d9a8f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184842"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="1888e-102">追蹤的安全性考量及實用秘訣</span><span class="sxs-lookup"><span data-stu-id="1888e-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="1888e-103">此主題描述如何保護敏感資訊以防公開，以及使用 WebHost 時的實用秘訣。</span><span class="sxs-lookup"><span data-stu-id="1888e-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="1888e-104">使用自訂追蹤接聽項來搭配 WebHost</span><span class="sxs-lookup"><span data-stu-id="1888e-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="1888e-105">如果您正在撰寫自己的追蹤接聽項，應該知道追蹤有可能在 Web 裝載服務的情況中遺失。</span><span class="sxs-lookup"><span data-stu-id="1888e-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="1888e-106">當 WebHost 進行回收，會關閉即時處理序以讓複本接手。</span><span class="sxs-lookup"><span data-stu-id="1888e-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="1888e-107">然而，視接聽項型別而定，這兩個處理序必須同時存取相同資源一段時間。</span><span class="sxs-lookup"><span data-stu-id="1888e-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="1888e-108">在此情況中，`XmlWriterTraceListener` 會為第二個處理序建立新的追蹤檔；而 Windows 事件追蹤則負責管理相同工作階段中的多個處理序，並存取相同的檔案。</span><span class="sxs-lookup"><span data-stu-id="1888e-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="1888e-109">如果您自己的接聽項無法提供類似的功能，當兩個處理序鎖住該檔案，追蹤可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="1888e-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="1888e-110">您應該同時了解到，自訂追蹤接聽項可以透過網路傳送追蹤與訊息，例如，傳送至遠端資料庫。</span><span class="sxs-lookup"><span data-stu-id="1888e-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="1888e-111">身為應用程式的部署者，您應該使用適當的存取控制來設定自訂接聽項。</span><span class="sxs-lookup"><span data-stu-id="1888e-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="1888e-112">您應該同時針對任何可以在遠端位置上公開的個人資訊套用安全性控制。</span><span class="sxs-lookup"><span data-stu-id="1888e-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="1888e-113">記錄敏感資訊</span><span class="sxs-lookup"><span data-stu-id="1888e-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="1888e-114">當訊息在範圍內時，追蹤就包含訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="1888e-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="1888e-115">啟用追蹤時，應用程式特定標頭中的個人資訊 (例如查詢字串) 和本文資訊 (例如信用卡號碼) 會在記錄檔中變得可見。</span><span class="sxs-lookup"><span data-stu-id="1888e-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="1888e-116">應用程式部署者負責強制針對組態和追蹤檔採取存取控制。</span><span class="sxs-lookup"><span data-stu-id="1888e-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="1888e-117">如果不要讓這類資訊變得可見，您應該停用追蹤，如果要共用追蹤記錄檔，則應該篩選掉部分資料。</span><span class="sxs-lookup"><span data-stu-id="1888e-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="1888e-118">下列秘訣有助於防止無意間公開追蹤檔內容：</span><span class="sxs-lookup"><span data-stu-id="1888e-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
-   <span data-ttu-id="1888e-119">確定在 WebHost 和自我裝載的情況下，記錄檔都受到存取控制清單 (ACL) 的保護。</span><span class="sxs-lookup"><span data-stu-id="1888e-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
-   <span data-ttu-id="1888e-120">您選擇的副檔名不可讓人透過 Web 要求就輕而易舉地取得檔案。</span><span class="sxs-lookup"><span data-stu-id="1888e-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="1888e-121">例如，.xml 副檔名就不是安全的選擇。</span><span class="sxs-lookup"><span data-stu-id="1888e-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="1888e-122">請參閱 IIS 管理手冊，查看可服務的副檔名清單。</span><span class="sxs-lookup"><span data-stu-id="1888e-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
-   <span data-ttu-id="1888e-123">指定絕對路徑做為記錄檔位置，此位置應該位於 WebHost vroot 公用目錄之外，以防止外部人員使用網頁瀏覽器存取記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1888e-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="1888e-124">根據預設，金鑰和個人可識別資訊 (PII)，例如使用者名稱和密碼，不會記錄在追蹤和記錄訊息中。</span><span class="sxs-lookup"><span data-stu-id="1888e-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="1888e-125">不過，電腦的系統管理員還是可以使用 Machine.config 檔案中 `enableLoggingKnownPII` 項目的 `machineSettings` 屬性，來允許電腦上執行的應用程式記錄已知的個人可識別資訊 (PII)，如下列所示：</span><span class="sxs-lookup"><span data-stu-id="1888e-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 <span data-ttu-id="1888e-126">然後，應用程式部署者可以使用 App.config 或 Web.config 檔案中的 `logKnownPii` 屬性，啟用 PII 記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1888e-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="1888e-127">只有在這兩個設定都是 `true` 時，才會啟用 PII 記錄。</span><span class="sxs-lookup"><span data-stu-id="1888e-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="1888e-128">結合兩個參數，提供了記錄每個應用程式已知 PII 的彈性。</span><span class="sxs-lookup"><span data-stu-id="1888e-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="1888e-129">您應該知道，在組態檔中指定兩個以上的自訂來源時，只會讀取第一個來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="1888e-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="1888e-130">其他的來源則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1888e-130">The others are ignored.</span></span> <span data-ttu-id="1888e-131">這表示，在下列的 App.config 檔案中，即使第二個來源已明確啟用 PII 記錄，但不會記錄這兩個來源的 PII。</span><span class="sxs-lookup"><span data-stu-id="1888e-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"   
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="1888e-132">如果`<machineSettings enableLoggingKnownPii="Boolean"/>`t:system.configuration.configurationerrorsexception 項目不在 Machine.config 檔案，系統會擲回<xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="1888e-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="1888e-133">只有在應用程式啟動或重新啟動時，才能讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="1888e-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="1888e-134">當這兩個屬性都設定為 `true` 時，啟動時會記錄事件。</span><span class="sxs-lookup"><span data-stu-id="1888e-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="1888e-135">如果 `logKnownPii` 設定為 `true`，但 `enableLoggingKnownPii` 設定為 `false`，也會記錄事件。</span><span class="sxs-lookup"><span data-stu-id="1888e-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="1888e-136">如需有關 PII 記錄的詳細資訊，請參閱[PII 安全性鎖定](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md)範例。</span><span class="sxs-lookup"><span data-stu-id="1888e-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="1888e-137">電腦的系統管理員和應用程式部署人員在使用這兩個參數時，應該特別小心謹慎。</span><span class="sxs-lookup"><span data-stu-id="1888e-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="1888e-138">如果啟用 PII 記錄，則會記錄安全性金鑰和 PII。</span><span class="sxs-lookup"><span data-stu-id="1888e-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="1888e-139">如果停用，敏感資料和應用程式特定資料仍然會記錄在訊息標頭和本文中。</span><span class="sxs-lookup"><span data-stu-id="1888e-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="1888e-140">如需隱私權和保護 PII 免於遭到公開的更完整討論，請參閱 <<c0> [ 使用者隱私權](https://go.microsoft.com/fwlink/?LinkID=94647)。</span><span class="sxs-lookup"><span data-stu-id="1888e-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://go.microsoft.com/fwlink/?LinkID=94647).</span></span>  
  
 <span data-ttu-id="1888e-141">此外，每次連線以進行連線導向的傳輸，或是每次以其他方式傳送訊息時，都會記錄一次訊息寄件者的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1888e-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="1888e-142">這不需要寄件者的同意就能進行。</span><span class="sxs-lookup"><span data-stu-id="1888e-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="1888e-143">但是，這種記錄行為只會發生在 [資訊] 或 [詳細資料] 追蹤層級中 (不屬於實際執行的預設或建議追蹤層級)，除了即時偵錯以外。</span><span class="sxs-lookup"><span data-stu-id="1888e-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1888e-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1888e-144">See Also</span></span>  
 [<span data-ttu-id="1888e-145">追蹤</span><span class="sxs-lookup"><span data-stu-id="1888e-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
