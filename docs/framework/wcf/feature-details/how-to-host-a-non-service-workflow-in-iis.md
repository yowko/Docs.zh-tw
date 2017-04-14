---
title: "HOW TO：在 IIS 中裝載非服務工作流程 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f362562c-767d-401b-8257-916616568fd4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# HOW TO：在 IIS 中裝載非服務工作流程
您可以在 IIS\/WAS 底下裝載非工作流程服務的工作流程。  當您需要裝載其他人所撰寫的工作流程時，這樣做就很有用。  例如，如果您重新裝載工作流程設計工具並允許使用者建立自己的工作流程。  在 IIS 中裝載非服務工作流程可支援許多功能，例如處理序回收、閒置關機、處理序健康狀態監控，以及訊息啟動。  在 IIS 中裝載的工作流程服務包含 <xref:System.ServiceModel.Activities.Receive> 活動，而且這些服務會在 IIS 收到訊息時啟動。  非服務工作流程不包含訊息活動，而且預設無法透過傳送訊息來啟動。  您必須從 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 衍生類別，並且定義包含作業的服務合約來建立工作流程執行個體。  本主題將逐步引導您建立簡單的工作流程、定義用戶端可用來啟動工作流程的服務合約，並且從使用服務合約的 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 衍生類別，以便接聽工作流程建立要求。  
  
### 建立簡單的工作流程  
  
1.  建立新的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 空方案，稱為 `CreationEndpointTest`。  
  
2.  將名為 `SimpleWorkflow` 的新 WCF 工作流程服務應用程式專案加入至此方案。  工作流程設計工具隨即開啟。  
  
3.  刪除 ReceiveRequest 和 SendResponse 活動。  這些活動就是讓工作流程成為工作流程服務的活動。  因為我們不要使用工作流程服務，所以不再需要它們。  
  
4.  將序列活動的 DisplayName 設定為 “Sequential Workflow”。  
  
5.  將 Service1.xamlx 重新命名為 Workflow1.xamlx。  
  
6.  按一下序列活動外部的設計工具，然後將 Name 和 ConfigurationName 屬性設定為 “Workflow1”。  
  
7.  將 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 中。  您可以在工具箱的 \[**基本**\] 區段中找到 <xref:System.Activities.Statements.WriteLine> 活動。  將 <xref:System.Activities.Statements.WriteLine> 活動的 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 “Hello, world”。  
  
     現在，工作流程的外觀應該如下圖所示。  
  
     ![簡單的工作流程](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")  
  
### 建立工作流程建立服務合約  
  
1.  將名為 `Shared` 的新類別庫專案加入至 `CreationEndpointTest` 方案。  
  
2.  將 System.ServiceModel.dll、System.Configuration 和 System.ServiceModel.Activities 的參考加入至 `Shared` 專案。  
  
3.  將 Class1.cs 檔案重新命名為 IWorkflowCreation.cs 並將下列程式碼複製到檔案。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     這個合約會定義兩項作業，而這兩項作業都會建立您剛才建立之非服務工作流程的新執行個體。  第一項作業會使用產生的執行個體 ID 來建立新的執行個體，而另一項作業可讓您針對新的工作流程執行個體指定執行個體 ID。  這兩種方法都允許您將參數傳入新的工作流程執行個體。  這個合約將由 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 公開，以便允許用戶端建立非服務工作流程的新執行個體。  
  
### 從 WorkflowHostingEndpoint 衍生類別  
  
1.  將衍生自 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 且名為 `CreationEndpoint` 的新類別加入至 `Shared` 專案。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  將名為 `defaultBaseUri` 的區域靜態 <xref:System.Uri> 變數加入至 `CreationEndpoint` 類別。  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  將下列建構函式加入至 `CreationEndpoint` 類別。  請注意，我們會在基底建構函式的呼叫中指定 `IWorkflowCreation` 服務合約。  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  將下列預設建構函式加入至 `CreationEndpoint` 類別。  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  將靜態 `DefaultBaseUri` 屬性加入至 `CreationEndpoint` 類別。  這個屬性將用來保存預設基底 URI \(如果沒有提供的話\)。  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  建立下列方法，以便取得要用於建立端點的預設繫結。  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  覆寫 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> 方法，以便傳回工作流程執行個體 ID。  如果 `Action` 標頭以 “Create” 為結尾，就會傳回空的 GUID。如果 `Action` 標頭以 “CreateWithInstanceId” 為結尾，則傳回傳入方法的 GUID。  否則，就會擲回 <xref:System.InvalidOperationException>。  這些 `Action` 標頭會對應至 `IWorkflowCreation` 服務合約中定義的兩項作業。  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  覆寫 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> 方法，以便建立 <xref:System.ServiceModel.Activities.WorkflowCreationContext> 並加入工作流程的任何引數、將執行個體 ID 傳送至用戶端，然後傳回 <xref:System.ServiceModel.Activities.WorkflowCreationContext>。  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### 建立標準端點項目，讓您設定 WorkflowCreationEndpoint  
  
1.  在 `CreationEndpoint` 專案中加入 Shared 的參考。  
  
2.  將衍生自 <xref:System.ServiceModel.Configuration.StandardEndpointElement> 且名為 `CreationEndpointElement` 的新類別加入至 `CreationEndpoint` 專案。  這個類別將代表 web.config 檔案中的 `CreationEndpoint`。  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  加入名為 `EndpointType` 的屬性，以便傳回端點的型別。  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  覆寫 <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> 方法，並傳回新的 `CreationEndpoint`。  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
  
    ```  
  
5.  多載 <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>、<xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>、<xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> 和 <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> 方法。  您只需要定義這些方法，不需要加入任何程式碼。  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  將 `CreationEndpoint` 的集合類別加入至 `CreationEndpoint` 專案中的 CreationEndpointElement.cs 檔案。  組態會使用這個類別，在 web.config 檔案中保存許多 `CreationEndpoint` 執行個體。  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  建置方案。  
  
### 在 IIS 中裝載工作流程  
  
1.  在 IIS 中建立名為 `MyCreationEndpoint` 的新應用程式。  
  
2.  將工作流程設計工具所產生的 workflow1.xaml 檔案複製到應用程式目錄並將它重新命名為 workflow1.xamlx。  
  
3.  將 shared.dll 和 CreationEndpoint.dll 檔案複製到應用程式的 bin 目錄 \(如果此目錄不存在，請建立 bin 目錄\)。  
  
4.  將 `CreationEndpoint` 專案中 Web.config 檔案的內容取代成下列程式碼。  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  在 `<system.web>` 項目後面加入下列組態程式碼，藉以註冊 `CreationEndpoint`。  
  
    ```  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
  
    ```  
  
     這樣就會註冊 `CreationEndpointCollection` 類別，因此您可以在 web.config 檔案中設定 `CreationEndpoint`。  
  
6.  用接聽傳入訊息的 `CreationEndpoint` 來加入 `<service>` 項目 \(在 \<\/extensions\> 標記後面\)。  
  
    ```  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
  
    ```  
  
7.  加入 \<behaviors\> 項目 \(在 \<\/services\> tag\) 標記後面\)，以便啟用服務中繼資料。  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
    ```  
  
8.  將 web.config 複製到您的 IIS 應用程式目錄。  
  
9. 測試以確認建立端點是否正常運作，方法是啟動 Internet Explorer 並瀏覽至 http:\/\/localhost\/MyCreationEndpoint\/Workflow1.xamlx。  Internet Explorer 應該會顯示下列畫面：  
  
     ![測試服務](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")  
  
### 建立將呼叫 CreationEndpoint 的用戶端。  
  
1.  將新的主控台應用程式加入至 `CreationEndpointTest` 方案。  
  
2.  加入 System.ServiceModel.dll、System.ServiceModel.Activities 和 `Shared` 專案的參考。  
  
3.  在 `Main` 方法中，建立型別為 `IWorkflowCreation` 的 <xref:System.ServiceModel.ChannelFactory%601> 並呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>。  這樣就會傳回 Proxy。  然後，您可以在該 Proxy 上呼叫 `Create`，以便建立在 IIS 底下裝載的工作流程執行個體：  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  執行 CreationEndpointClient。  輸出看起來應該如下所示：  
  
    ```Output  
  
                Workflow Instance created using CreationEndpoint added in config.  執行個體 Id：0875dac0-2b8b-473e-b3cc-abcb235e9693  
    按下 Return 結束...    
    ```  
  
    > [!NOTE]
    >  您不會看見工作流程的輸出，因為它在沒有任何主控台輸出的 IIS 底下執行。  
  
## 範例  
 下面是此範例的完整程式碼。  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
  
```  
  
 此範例可能會產生混淆，因為您從未實作可實作 `IWorkflowCreation` 的服務。  這是因為 `CreationEndpoint` 為您實作了此服務。  
  
## 請參閱  
 [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [在網際網路資訊服務中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)   
 [網際網路資訊服務裝載最佳做法](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)   
 [Internet Information Service 裝載指示](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)   
 [Windows 工作流程架構](../../../../docs/framework/windows-workflow-foundation//architecture.md)   
 [WorkflowHostingEndpoint 繼續書籤](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)   
 [重新裝載工作流程設計工具](../../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [Windows Workflow 概觀](../../../../docs/framework/windows-workflow-foundation//overview.md)