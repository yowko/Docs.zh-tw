---
title: HOW TO：實作探索 Proxy
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: 0928db476c759ac76a117485586d43c2414e2945
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635281"
---
# <a name="how-to-implement-a-discovery-proxy"></a>HOW TO：實作探索 Proxy
本主題說明如何實作探索 Proxy。 如需 Windows Communication Foundation (WCF) 中的 [探索] 功能的詳細資訊，請參閱[WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)。 探索 Proxy 可透過建立延伸類別的方式來實作，該類別可擴充<xref:System.ServiceModel.Discovery.DiscoveryProxy> 抽象類別。 許多其他支援類別都已在此範例中定義和使用。 `OnResolveAsyncResult`、`OnFindAsyncResult` 和 `AsyncResult`。 這些類別會實作 <xref:System.IAsyncResult> 介面。 如需詳細資訊<xref:System.IAsyncResult>請參閱 < [System.IAsyncResult 介面](xref:System.IAsyncResult)。

 本主題將實作探索 Proxy 分為三個主要部分：

- 定義類別，包含資料存放區並可擴充抽象 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 類別。

- 實作 Helper `AsyncResult` 類別。

- 裝載探索 Proxy。

### <a name="to-create-a-new-console-application-project"></a>若要建立新的主控台應用程式專案

1. 啟動 Visual Studio 2012。

2. 建立新的主控台應用程式專案。 將專案命名為 `DiscoveryProxy`，並將方案命名為 `DiscoveryProxyExample`。

3. 將下列參考加入至專案中

    1. System.ServiceModel.dll

    2. System.Servicemodel.Discovery.dll

    > [!CAUTION]
    >  確定您參考的組件為 4.0 版或更新版本。

### <a name="to-implement-the-proxydiscoveryservice-class"></a>若要實作 ProxyDiscoveryService 類別

1. 將新的程式碼檔案加入至專案，並將其命名為 DiscoveryProxy.cs。

2. 將下列 `using` 陳述式加入至 DiscoveryProxy.cs。

    ```
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. 從 `DiscoveryProxyService` 衍生 <xref:System.ServiceModel.Discovery.DiscoveryProxy>。 將 `ServiceBehavior` 屬性套用至類別，如下列範例所示。

    ```
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. 在 `DiscoveryProxy` 類別內定義字典以保存已註冊的服務。

    ```
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. 定義初始化字典的建構函式。

    ```
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a>若要定義用來更新探索 Proxy 快取的方法

1. 實作 `AddOnlineservice` 方法，將服務加入至快取。 Proxy 每次收到公告訊息時都會呼叫此動作。

    ```
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
            }
    ```

2. 實作 `RemoveOnlineService` 方法，這個方法可用來移除來自快取的服務。

    ```
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                if (endpointDiscoveryMetadata != null)
                {
                    lock (this.onlineServices)
                    {
                        this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                    }

                    PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
                }
            }
    ```

3. 實作 `MatchFromOnlineService` 方法，這些方法會嘗試比對某個服務與字典中的服務。

    ```
    void MatchFromOnlineService(FindRequestContext findRequestContext)
            {
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                        {
                            findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                        }
                    }
                }
            }
    ```

    ```
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
            {
                EndpointDiscoveryMetadata matchingEndpoint = null;
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (criteria.Address == endpointDiscoveryMetadata.Address)
                        {
                            matchingEndpoint = endpointDiscoveryMetadata;
                        }
                    }
                }
                return matchingEndpoint;
            }
    ```

4. 實作 `PrintDiscoveryMetadata` 方法，這個方法可提供使用者探索 Proxy 進行中的主控台文字輸出。

    ```
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
            {
                Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
                foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
                {
                    Console.WriteLine("** " + contractName.ToString());
                    break;
                }
                Console.WriteLine("**** Operation Completed");
            }
    ```

5. 將下列 AsyncResult 類別加入至 DiscoveryProxyService。 這些類別用於區分不同的非同步作業結果。

    ```
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
            {
                public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
            {
                public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnFindAsyncResult : AsyncResult
            {
                public OnFindAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnFindAsyncResult>(result);
                }
            }

            sealed class OnResolveAsyncResult : AsyncResult
            {
                EndpointDiscoveryMetadata matchingEndpoint;

                public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.matchingEndpoint = matchingEndpoint;
                    this.Complete(true);
                }

                public static EndpointDiscoveryMetadata End(IAsyncResult result)
                {
                    OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                    return thisPtr.matchingEndpoint;
                }
            }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a>若要定義可實作探索 Proxy 功能的方法

1. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 收到線上公告訊息時，就會呼叫此方法。

    ```
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.AddOnlineService(endpointDiscoveryMetadata);
                return new OnOnlineAnnouncementAsyncResult(callback, state);
            }
    ```

2. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 完成處理公告訊息時，就會呼叫此方法。

    ```
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
            {
                OnOnlineAnnouncementAsyncResult.End(result);
            }
    ```

3. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 收到離線公告訊息時，就會呼叫此方法。

    ```
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.RemoveOnlineService(endpointDiscoveryMetadata);
                return new OnOfflineAnnouncementAsyncResult(callback, state);
            }
    ```

4. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 完成處理離線公告訊息時，就會呼叫此方法。

    ```
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
            {
                OnOfflineAnnouncementAsyncResult.End(result);
            }
    ```

5. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 收到尋找要求時，就會呼叫此方法。

    ```
    // OnBeginFind method is called when a Probe request message is received by the Proxy
            protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
            {
                this.MatchFromOnlineService(findRequestContext);
                return new OnFindAsyncResult(callback, state);
            }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 完成處理尋找要求時，就會呼叫此方法。

    ```
    protected override void OnEndFind(IAsyncResult result)
            {
                OnFindAsyncResult.End(result);
            }
    ```

7. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 收到解析訊息時，就會呼叫此方法。

    ```
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
            protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
            {
                return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
            }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. 覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> 方法。 當探索 Proxy 完成處理解析訊息時，就會呼叫此方法。

    ```
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

 OnBegin. / OnEnd. 方法提供後續探索作業的邏輯。 例如，<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> 和 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> 方法可實作探索 Proxy 的尋找邏輯。 當探索 Proxy 收到檢測訊息時，便會執行這些方法來傳送回應至用戶端。 您可以修改尋找邏輯，例如，您可透過演算法或應用程式特定 XML 中繼資料剖析的方式，加入自訂範圍比對，做為尋找作業的一部分。

### <a name="to-implement-the-asyncresult-class"></a>若要實作 AsyncResult 類別

1. 定義抽象基底類別 AsyncResult，這個類別用於衍生各種非同步結果類別。

2. 建立名為 AsyncResult.cs 的新程式碼檔案。

3. 將下列 `using` 陳述式加入至 AsyncResult.cs。

    ```
    using System;
    using System.Threading;
    ```

4. 加入下列 AsyncResult 類別。

    ```
    abstract class AsyncResult : IAsyncResult
        {
            AsyncCallback callback;
            bool completedSynchronously;
            bool endCalled;
            Exception exception;
            bool isCompleted;
            ManualResetEvent manualResetEvent;
            object state;
            object thisLock;

            protected AsyncResult(AsyncCallback callback, object state)
            {
                this.callback = callback;
                this.state = state;
                this.thisLock = new object();
            }

            public object AsyncState
            {
                get
                {
                    return state;
                }
            }

            public WaitHandle AsyncWaitHandle
            {
                get
                {
                    if (manualResetEvent != null)
                    {
                        return manualResetEvent;
                    }
                    lock (ThisLock)
                    {
                        if (manualResetEvent == null)
                        {
                            manualResetEvent = new ManualResetEvent(isCompleted);
                        }
                    }
                    return manualResetEvent;
                }
            }

            public bool CompletedSynchronously
            {
                get
                {
                    return completedSynchronously;
                }
            }

            public bool IsCompleted
            {
                get
                {
                    return isCompleted;
                }
            }

            object ThisLock
            {
                get
                {
                    return this.thisLock;
                }
            }

            protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
                where TAsyncResult : AsyncResult
            {
                if (result == null)
                {
                    throw new ArgumentNullException("result");
                }

                TAsyncResult asyncResult = result as TAsyncResult;

                if (asyncResult == null)
                {
                    throw new ArgumentException("Invalid async result.", "result");
                }

                if (asyncResult.endCalled)
                {
                    throw new InvalidOperationException("Async object already ended.");
                }

                asyncResult.endCalled = true;

                if (!asyncResult.isCompleted)
                {
                    asyncResult.AsyncWaitHandle.WaitOne();
                }

                if (asyncResult.manualResetEvent != null)
                {
                    asyncResult.manualResetEvent.Close();
                }

                if (asyncResult.exception != null)
                {
                    throw asyncResult.exception;
                }

                return asyncResult;
            }

            protected void Complete(bool completedSynchronously)
            {
                if (isCompleted)
                {
                    throw new InvalidOperationException("This async result is already completed.");
                }

                this.completedSynchronously = completedSynchronously;

                if (completedSynchronously)
                {
                    this.isCompleted = true;
                }
                else
                {
                    lock (ThisLock)
                    {
                        this.isCompleted = true;
                        if (this.manualResetEvent != null)
                        {
                            this.manualResetEvent.Set();
                        }
                    }
                }

                if (callback != null)
                {
                    callback(this);
                }
            }

            protected void Complete(bool completedSynchronously, Exception exception)
            {
                this.exception = exception;
                Complete(completedSynchronously);
            }
        }
    ```

### <a name="to-host-the-discoveryproxy"></a>若要裝載 DiscoveryProxy

1. 開啟 DiscoveryProxyExample 專案中的 Program.cs 檔案。

2. 加入下列 `using` 陳述式。

    ```
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. 在 `Main()` 方法中，加入下列程式碼。 這樣做可建立 `DiscoveryProxy` 類別的執行個體。

    ```
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

                // Host the DiscoveryProxy service
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. 接著，加入下列程式碼以加入探索端點與公告端點。

    ```
    try
              {
                  // Add DiscoveryEndpoint to receive Probe and Resolve messages
                  DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                  discoveryEndpoint.IsSystemEndpoint = false;

                  // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                  AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                  proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                  proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                  proxyServiceHost.Open();

                  Console.WriteLine("Proxy Service started.");
                  Console.WriteLine();
                  Console.WriteLine("Press <ENTER> to terminate the service.");
                  Console.WriteLine();
                  Console.ReadLine();

                  proxyServiceHost.Close();
              }
              catch (CommunicationException e)
              {
                  Console.WriteLine(e.Message);
              }
              catch (TimeoutException e)
              {
                  Console.WriteLine(e.Message);
              }

              if (proxyServiceHost.State != CommunicationState.Closed)
              {
                  Console.WriteLine("Aborting the service...");
                  proxyServiceHost.Abort();
              }
    ```

 您已經完成實作探索 Proxy。 繼續前往[How to:實作以探索 Proxy 註冊的可探索服務](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)。

## <a name="example"></a>範例
 以下是本主題所使用之程式碼的完整清單。

```
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    if (manualResetEvent == null)
                    {
                        manualResetEvent = new ManualResetEvent(isCompleted);
                    }
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [如何：實作以探索 Proxy 註冊的可探索服務](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [如何：實作使用探索 Proxy 尋找服務的用戶端應用程式](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
- [如何：測試探索 Proxy](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)
