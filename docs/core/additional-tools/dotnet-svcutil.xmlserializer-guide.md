# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>在 .NET Core 上使用 dotnet-svcutil.xmlserializer

## <a name="prerequisites"></a>必要條件

dotnet-svcutil.xmlserializer 運作需要下列項目。 

* [.NET Core 2.1 SDK 或更新版本](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [.NET Core 執行階段 2.1 或更新版本](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

您可以使用命令 `dotnet --info` 來檢查已安裝的 .NET Core SDK 和執行階段版本。

若要在 .NET Core 主控台應用程式中使用 dotnet svcutil.xmlserializer：

1. 使用 .NET Framework 中的預設範本「WCF 服務應用程式」建立名為 'MyWCFService' 的 WCF 服務。  在服務方法上新增 ```[XmlSerializerFormat]``` 屬性，如下所示
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. 建立一個以 netcoreapp 2.1 為目標的 .NET Core 主控台應用程式，例如，使用下列命令建立名為 'MyWCFClient' 的應用程式，
    ```
    dotnet new console --name MyWCFClient
    ```
    請確定您的 csproj 以 netcoreapp 2.1 為目標。 這是使用 .csproj 檔案中的下列 XML 元素完成的
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. 透過執行下列命令，新增對 System.ServiceModel.Http 的套件參考：
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. 新增 WCF 用戶端程式碼：
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
5. 編輯 .csproj 檔案，並新增對 dotnet-svcutil.xmlserializer 套件的參考。 例如：

    i. 執行命令：`dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`

    ii. 在 MyWCFClient.csproj 中新增下列幾行，
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. 執行 `dotnet build` 建置應用程式。 如果所有項目都成功，則會在輸出資料夾中產生名為 MyWCFClient.XmlSerializers.dll 的組件。 如果此工具無法產生組件，您將在建置輸出中看到警告。

7. 啟動 WCF 服務，例如，透過在瀏覽器中執行 http://localhost:2561/Service1.svc。 然後啟動用戶端應用程式，它將在執行階段自動載入和使用預先產生的序列化程式。
