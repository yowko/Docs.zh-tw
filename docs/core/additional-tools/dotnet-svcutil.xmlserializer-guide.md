---
title: 在 .NET Core 上使用 dotnet-svcutil.xmlserializer
description: 了解如何使用 `dotnet-svcutil.xmlserializer` NuGet 套件預先產生 .NET Core 專案的序列化組件。
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 375a5ad5660658431c0d327e55513024823a6eee
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632191"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>在 .NET Core 上使用 dotnet-svcutil.xmlserializer

`dotnet-svcutil.xmlserializer` NuGet 套件可預先產生 .NET Core 專案的序列化組件。 它會為用戶端應用程式中由 WCF 服務合約使用且可由 XmlSerializer 序列化的類型預先產生 C# 序列化程式碼。 這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。

## <a name="prerequisites"></a>必要條件

* [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 或更新版本
* 您慣用的程式碼編輯器

您可以使用命令 `dotnet --info` 來檢查已安裝的 .NET Core SDK 和執行階段版本。

## <a name="getting-started"></a>使用者入門

若要在 .NET Core 主控台應用程式中使用 `dotnet-svcutil.xmlserializer`：

1. 使用 .NET Framework 中的預設範本「WCF 服務應用程式」建立名為 'MyWCFService' 的 WCF 服務。 在服務方法上新增 `[XmlSerializerFormat]` 屬性，如下所示：

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. 建立以 .NET Core 2.1 或更新版本為目標的 .NET Core 主控台應用程式作為 WCF 用戶端應用程式。 例如，使用下列命令建立名為 'MyWCFClient' 的應用程式：

    ```console
    dotnet new console --name MyWCFClient
    ```

    若要確定您的專案是以 .NET Core 2.1 或更新版本為目標，請檢查專案檔中的 `TargetFramework` XML 元素：

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. 執行下列命令，新增對 `System.ServiceModel.Http` 的套件參考：

    ```console
    dotnet add package System.ServiceModel.Http
    ```

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

5. 執行下列命令，新增對 `dotnet-svcutil.xmlserializer` 套件的參考：
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    執行命令應該會將一個項目新增至您的專案檔，如下所示：
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. 執行 `dotnet build` 建置應用程式。 如果所有項目都成功，則會在輸出資料夾中產生名為 *MyWCFClient.XmlSerializers.dll* 的組件。 如果此工具無法產生組件，您將在建置輸出中看到警告。

7. 啟動 WCF 服務，例如在瀏覽器中執行 `http://localhost:2561/Service1.svc`。 然後啟動用戶端應用程式，它將在執行階段自動載入和使用預先產生的序列化程式。
