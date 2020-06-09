---
title: 使用 Windows 市集用戶端應用程式存取 WCF 服務
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: ff6638936f476bd8fe75a065d3e61e96790cb7f4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597692"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="9be64-102">使用 Windows 市集用戶端應用程式存取 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="9be64-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="9be64-103">Windows 8 引入新的應用程式型別，稱為 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be64-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="9be64-104">這些應用程式都是以觸控式螢幕介面為設計主軸。</span><span class="sxs-lookup"><span data-stu-id="9be64-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="9be64-105">.NET Framework 4.5 可讓 Windows 市集應用程式呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="9be64-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="9be64-106">Windows 市集應用程式中的 WCF 支援</span><span class="sxs-lookup"><span data-stu-id="9be64-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="9be64-107">Windows 市集應用程式中提供部分的 WCF 功能，請參閱下列各節中的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9be64-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9be64-108">使用 WinRT 新聞訂閱應用程式開發介面，而不使用由 WCF 所公開的介面。</span><span class="sxs-lookup"><span data-stu-id="9be64-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="9be64-109">如需詳細資訊，請參閱 [WinRT 新聞訂閱應用程式開發介面](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="9be64-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9be64-110">不支援使用 [加入服務參考]，將 Web 服務參考加入 Windows 執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="9be64-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="9be64-111">支援的繫結</span><span class="sxs-lookup"><span data-stu-id="9be64-111">Supported Bindings</span></span>  
 <span data-ttu-id="9be64-112">Windows 市集應用程式支援下列 WCF 繫結：</span><span class="sxs-lookup"><span data-stu-id="9be64-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="9be64-113">Windows 市集應用程式支援下列繫結項目</span><span class="sxs-lookup"><span data-stu-id="9be64-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="9be64-114">同時支援二進位和文字編碼方式。</span><span class="sxs-lookup"><span data-stu-id="9be64-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="9be64-115">支援所有 WCF 傳輸模式。</span><span class="sxs-lookup"><span data-stu-id="9be64-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="9be64-116">如需詳細資訊，請參閱 [Streaming Message Transfer](streaming-message-transfer.md)。</span><span class="sxs-lookup"><span data-stu-id="9be64-116">For more information see, [Streaming Message Transfer](streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="9be64-117">中的 [</span><span class="sxs-lookup"><span data-stu-id="9be64-117">Add Service Reference</span></span>  
 <span data-ttu-id="9be64-118">若要從 Windows 市集應用程式呼叫 WCF 服務，請使用 Visual Studio 2012 的 [加入服務參考] 功能。</span><span class="sxs-lookup"><span data-stu-id="9be64-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="9be64-119">在 Windows 市集應用程式中執行時，您會發現 [加入服務參考] 的功能有一些變更。</span><span class="sxs-lookup"><span data-stu-id="9be64-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="9be64-120">首先是沒有產生組態檔。</span><span class="sxs-lookup"><span data-stu-id="9be64-120">First no configuration file is generated.</span></span> <span data-ttu-id="9be64-121">Windows 市集應用程式不使用組態檔，因此必須在程式碼中進行設定。</span><span class="sxs-lookup"><span data-stu-id="9be64-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="9be64-122">您可以在 [加入服務參考] 產生的 References.cs 檔案中找到這個組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="9be64-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="9be64-123">若要查看此檔案，請務必選取 [方案瀏覽器] 中的 [顯示所有檔案]。</span><span class="sxs-lookup"><span data-stu-id="9be64-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="9be64-124">檔案位於 [服務參考] 底下，專案內的 Reference.svcmap 節點中。</span><span class="sxs-lookup"><span data-stu-id="9be64-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="9be64-125">在 Windows 市集應用程式中，針對 WCF 服務產生的所有作業都會使用以工作為基礎的非同步模式，且都是非同步。</span><span class="sxs-lookup"><span data-stu-id="9be64-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="9be64-126">如需詳細資訊，請參閱[非同步工作-使用工作簡化非同步程式設計](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks)。</span><span class="sxs-lookup"><span data-stu-id="9be64-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="9be64-127">由於組態現在是以程式碼來產生，因此每次服務參考更新時，在 Reference.cs 檔案中所做的任何變更都會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="9be64-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="9be64-128">若要補救這種情況，您可以在用戶端 Proxy 類別中實作部分方法，讓組態程式碼由部分方法來產生。</span><span class="sxs-lookup"><span data-stu-id="9be64-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="9be64-129">部分方法的宣告如下：</span><span class="sxs-lookup"><span data-stu-id="9be64-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="9be64-130">然後，您可以在用戶端 Proxy 類別中，實作這個部分方法並變更繫結或端點，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9be64-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="9be64-131">序列化</span><span class="sxs-lookup"><span data-stu-id="9be64-131">Serialization</span></span>  
 <span data-ttu-id="9be64-132">Windows 市集應用程式支援下列序列化程式：</span><span class="sxs-lookup"><span data-stu-id="9be64-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="9be64-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="9be64-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="9be64-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="9be64-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="9be64-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="9be64-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9be64-136">XmlDictionaryWriter.Write(DateTime) 現在會將 DateTime 物件當做字串寫入。</span><span class="sxs-lookup"><span data-stu-id="9be64-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="9be64-137">安全性</span><span class="sxs-lookup"><span data-stu-id="9be64-137">Security</span></span>  

<span data-ttu-id="9be64-138">Windows Store 應用程式支援下列安全性模式：</span><span class="sxs-lookup"><span data-stu-id="9be64-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="9be64-139">Windows Store 應用程式支援下列用戶端認證類型：</span><span class="sxs-lookup"><span data-stu-id="9be64-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="9be64-140">無</span><span class="sxs-lookup"><span data-stu-id="9be64-140">None</span></span>  
  
2. <span data-ttu-id="9be64-141">基本</span><span class="sxs-lookup"><span data-stu-id="9be64-141">Basic</span></span>  
  
3. <span data-ttu-id="9be64-142">Digest</span><span class="sxs-lookup"><span data-stu-id="9be64-142">Digest</span></span>  
  
4. <span data-ttu-id="9be64-143">交涉</span><span class="sxs-lookup"><span data-stu-id="9be64-143">Negotiate</span></span>  
  
5. <span data-ttu-id="9be64-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="9be64-144">NTLM</span></span>  
  
6. <span data-ttu-id="9be64-145">Windows</span><span class="sxs-lookup"><span data-stu-id="9be64-145">Windows</span></span>  
  
7. <span data-ttu-id="9be64-146">使用者名稱 (訊息安全性)</span><span class="sxs-lookup"><span data-stu-id="9be64-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="9be64-147">Windows (傳輸安全性)</span><span class="sxs-lookup"><span data-stu-id="9be64-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="9be64-148">若要讓 Windows 市集應用程式存取和傳送預設 Windows 認證，您必須在 Package.appmanifest 檔案中啟用這個功能。</span><span class="sxs-lookup"><span data-stu-id="9be64-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="9be64-149">開啟此檔案並選取 [功能] 索引標籤，然後選取 [預設的 Windows 認證]。</span><span class="sxs-lookup"><span data-stu-id="9be64-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="9be64-150">這可讓應用程式連接至需要網域認證的內部網路資源。</span><span class="sxs-lookup"><span data-stu-id="9be64-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9be64-151">為了讓 Windows Store 應用程式進行跨電腦呼叫，您必須啟用另一個稱為「家庭/工作網路」的功能。</span><span class="sxs-lookup"><span data-stu-id="9be64-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="9be64-152">此設定也位於 [功能] 索引標籤下的 appmanifest 檔案中。請選取 [家用/工作網路] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9be64-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="9be64-153">這可提供應用程式對使用者所信任之位置 (例如，家裡或公司) 的網路進行傳入及傳出存取的權限。</span><span class="sxs-lookup"><span data-stu-id="9be64-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="9be64-154">永遠封鎖關鍵的傳入連接埠。</span><span class="sxs-lookup"><span data-stu-id="9be64-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="9be64-155">如果是存取網際網路上的服務，您還必須啟用網際網路 (用戶端) 功能。</span><span class="sxs-lookup"><span data-stu-id="9be64-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="9be64-156">其他</span><span class="sxs-lookup"><span data-stu-id="9be64-156">Misc</span></span>  
 <span data-ttu-id="9be64-157">Windows 市集應用程式支援使用下列類別：</span><span class="sxs-lookup"><span data-stu-id="9be64-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="9be64-158">定義服務合約</span><span class="sxs-lookup"><span data-stu-id="9be64-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="9be64-159">建議您只定義使用以工作為基礎之非同步模式的非同步服務作業。</span><span class="sxs-lookup"><span data-stu-id="9be64-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="9be64-160">這樣可以確保 Windows 市集應用程式在呼叫服務作業時仍能保持回應。</span><span class="sxs-lookup"><span data-stu-id="9be64-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9be64-161">雖然定義同步作業並不會擲回例外狀況，還是強烈建議您只定義非同步作業。</span><span class="sxs-lookup"><span data-stu-id="9be64-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="9be64-162">從 Windows 市集應用程式呼叫 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="9be64-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="9be64-163">正如前面提到的，所有組態都必須在所產生 Proxy 類別的 GetBindingForEndpoint 方法中，以程式碼來設定。</span><span class="sxs-lookup"><span data-stu-id="9be64-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="9be64-164">呼叫服務作業的方式與呼叫任何以工作為基礎的非同步方法相同，如下列程式碼片段中所示。</span><span class="sxs-lookup"><span data-stu-id="9be64-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="9be64-165">請注意，在進行非同步呼叫的方法上使用 async 關鍵字，並在呼叫非同步方法時使用 await 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9be64-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be64-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="9be64-166">See also</span></span>

- [<span data-ttu-id="9be64-167">Windows 市集應用程式中的 WCF 部落格</span><span class="sxs-lookup"><span data-stu-id="9be64-167">WCF in Windows Store Apps Blog</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [<span data-ttu-id="9be64-168">WCF Windows 市集用戶端與安全性</span><span class="sxs-lookup"><span data-stu-id="9be64-168">WCF Windows Store Clients and Security</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [<span data-ttu-id="9be64-169">Windows 市集應用程式與跨電腦呼叫</span><span class="sxs-lookup"><span data-stu-id="9be64-169">Windows Store Apps and Cross Machine Calls</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="9be64-170">從 Windows 市集應用程式呼叫在 Azure 中部署的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="9be64-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="9be64-171">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="9be64-171">Programming WCF Security</span></span>](programming-wcf-security.md)
- [<span data-ttu-id="9be64-172">繫結</span><span class="sxs-lookup"><span data-stu-id="9be64-172">Bindings</span></span>](../bindings.md)
