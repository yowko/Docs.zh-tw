# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="95628-101">在 .NET Core 上使用 dotnet-svcutil.xmlserializer</span><span class="sxs-lookup"><span data-stu-id="95628-101">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95628-102">必要條件</span><span class="sxs-lookup"><span data-stu-id="95628-102">Prerequisites</span></span>

<span data-ttu-id="95628-103">dotnet-svcutil.xmlserializer 運作需要下列項目。</span><span class="sxs-lookup"><span data-stu-id="95628-103">The following is required for dotnet-svcutil.xmlserializer to work.</span></span> 

* [<span data-ttu-id="95628-104">.NET Core 2.1 SDK 或更新版本</span><span class="sxs-lookup"><span data-stu-id="95628-104">.NET Core 2.1 SDK or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [<span data-ttu-id="95628-105">.NET Core 執行階段 2.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="95628-105">.NET Core Runtime 2.1 or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

<span data-ttu-id="95628-106">您可以使用命令 `dotnet --info` 來檢查已安裝的 .NET Core SDK 和執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="95628-106">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

<span data-ttu-id="95628-107">若要在 .NET Core 主控台應用程式中使用 dotnet svcutil.xmlserializer：</span><span class="sxs-lookup"><span data-stu-id="95628-107">To use dotnet-svcutil.xmlserializer in a .NET Core console application:</span></span>

1. <span data-ttu-id="95628-108">使用 .NET Framework 中的預設範本「WCF 服務應用程式」建立名為 'MyWCFService' 的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="95628-108">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span>  <span data-ttu-id="95628-109">在服務方法上新增 ```[XmlSerializerFormat]``` 屬性，如下所示</span><span class="sxs-lookup"><span data-stu-id="95628-109">Add ```[XmlSerializerFormat]``` attribute on the service method like the following</span></span>
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. <span data-ttu-id="95628-110">建立一個以 netcoreapp 2.1 為目標的 .NET Core 主控台應用程式，例如，使用下列命令建立名為 'MyWCFClient' 的應用程式，</span><span class="sxs-lookup"><span data-stu-id="95628-110">Create a .NET Core console application as WCF client application that targets at netcoreapp 2.1, e.g. create an app named 'MyWCFClient' with the command,</span></span>
    ```
    dotnet new console --name MyWCFClient
    ```
    <span data-ttu-id="95628-111">請確定您的 csproj 以 netcoreapp 2.1 為目標。</span><span class="sxs-lookup"><span data-stu-id="95628-111">Make sure your csproj targets a netcoreapp 2.1.</span></span> <span data-ttu-id="95628-112">這是使用 .csproj 檔案中的下列 XML 元素完成的</span><span class="sxs-lookup"><span data-stu-id="95628-112">This is done using the following XML element in your .csproj file</span></span>
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. <span data-ttu-id="95628-113">透過執行下列命令，新增對 System.ServiceModel.Http 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="95628-113">Add a package reference to System.ServiceModel.Http by running the following command:</span></span>
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. <span data-ttu-id="95628-114">新增 WCF 用戶端程式碼：</span><span class="sxs-lookup"><span data-stu-id="95628-114">Add the WCF Client code:</span></span>
    ```csharp
    using System.ServiceModel;
    
    class Program
    {
        static void Main(string[] args)
        {
            var myBinding = new BasicHttpBinding();
            var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
            var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
            IService1 client = myChannelFactory.CreateChannel();
            string s = client.GetData(1);
            ((ICommunicationObject)client).Close();
        }
    }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
5. <span data-ttu-id="95628-115">編輯 .csproj 檔案，並新增對 dotnet-svcutil.xmlserializer 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="95628-115">Edit the .csproj file and add a reference to the dotnet-svcutil.xmlserializer package.</span></span> <span data-ttu-id="95628-116">例如：</span><span class="sxs-lookup"><span data-stu-id="95628-116">For example:</span></span>

    <span data-ttu-id="95628-117">i.</span><span class="sxs-lookup"><span data-stu-id="95628-117">i.</span></span> <span data-ttu-id="95628-118">執行命令：`dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span><span class="sxs-lookup"><span data-stu-id="95628-118">Run command: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span></span>

    <span data-ttu-id="95628-119">ii.</span><span class="sxs-lookup"><span data-stu-id="95628-119">ii.</span></span> <span data-ttu-id="95628-120">在 MyWCFClient.csproj 中新增下列幾行，</span><span class="sxs-lookup"><span data-stu-id="95628-120">Add the following lines in MyWCFClient.csproj,</span></span>
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="95628-121">執行 `dotnet build` 建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="95628-121">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="95628-122">如果所有項目都成功，則會在輸出資料夾中產生名為 MyWCFClient.XmlSerializers.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="95628-122">If everything succeeds, an assembly named MyWCFClient.XmlSerializers.dll will be generated in the output folder.</span></span> <span data-ttu-id="95628-123">如果此工具無法產生組件，您將在建置輸出中看到警告。</span><span class="sxs-lookup"><span data-stu-id="95628-123">You will see warnings in the build output if the tool failed to generate the assembly.</span></span>

7. <span data-ttu-id="95628-124">啟動 WCF 服務，例如，透過在瀏覽器中執行 http://localhost:2561/Service1.svc。</span><span class="sxs-lookup"><span data-stu-id="95628-124">Start the WCF service e.g. by running http://localhost:2561/Service1.svc in the browser.</span></span> <span data-ttu-id="95628-125">然後啟動用戶端應用程式，它將在執行階段自動載入和使用預先產生的序列化程式。</span><span class="sxs-lookup"><span data-stu-id="95628-125">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
