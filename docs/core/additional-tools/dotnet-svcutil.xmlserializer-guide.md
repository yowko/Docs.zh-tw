---
title: 在 .NET Core 上使用 dotnet-svcutil.xmlserializer
description: 了解如何使用 `dotnet-svcutil.xmlserializer` NuGet 套件預先產生 .NET Core 專案的序列化組件。
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: f5ffed47079a3ee122c7784d0c61c4d40461ba26
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235536"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="44ca4-103">在 .NET Core 上使用 dotnet-svcutil.xmlserializer</span><span class="sxs-lookup"><span data-stu-id="44ca4-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="44ca4-104">`dotnet-svcutil.xmlserializer` NuGet 套件可預先產生 .NET Core 專案的序列化組件。</span><span class="sxs-lookup"><span data-stu-id="44ca4-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="44ca4-105">它會為用戶端應用程式中由 WCF 服務合約使用且可由 XmlSerializer 序列化的類型預先產生 C# 序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="44ca4-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="44ca4-106">這可改進當序列化或還原序列化那些類型的物件時的 XML 序列化啟動效能。</span><span class="sxs-lookup"><span data-stu-id="44ca4-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="44ca4-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="44ca4-107">Prerequisites</span></span>

* <span data-ttu-id="44ca4-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="44ca4-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="44ca4-109">您慣用的程式碼編輯器</span><span class="sxs-lookup"><span data-stu-id="44ca4-109">Your favorite code editor</span></span>

<span data-ttu-id="44ca4-110">您可以使用命令 `dotnet --info` 來檢查已安裝的 .NET Core SDK 和執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="44ca4-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="44ca4-111">使用者入門</span><span class="sxs-lookup"><span data-stu-id="44ca4-111">Getting started</span></span>

<span data-ttu-id="44ca4-112">若要在 .NET Core 主控台應用程式中使用 `dotnet-svcutil.xmlserializer`：</span><span class="sxs-lookup"><span data-stu-id="44ca4-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="44ca4-113">使用 .NET Framework 中的預設範本「WCF 服務應用程式」建立名為 'MyWCFService' 的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="44ca4-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="44ca4-114">在服務方法上新增 `[XmlSerializerFormat]` 屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="44ca4-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="44ca4-115">建立以 .NET Core 2.1 或更新版本為目標的 .NET Core 主控台應用程式作為 WCF 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="44ca4-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="44ca4-116">例如，使用下列命令建立名為 'MyWCFClient' 的應用程式：</span><span class="sxs-lookup"><span data-stu-id="44ca4-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```console
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="44ca4-117">若要確定您的專案是以 .NET Core 2.1 或更新版本為目標，請檢查專案檔中的 `TargetFramework` XML 元素：</span><span class="sxs-lookup"><span data-stu-id="44ca4-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="44ca4-118">執行下列命令，新增對 `System.ServiceModel.Http` 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="44ca4-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="44ca4-119">新增 WCF 用戶端程式碼：</span><span class="sxs-lookup"><span data-stu-id="44ca4-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="44ca4-120">執行下列命令，新增對 `dotnet-svcutil.xmlserializer` 套件的參考：</span><span class="sxs-lookup"><span data-stu-id="44ca4-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="44ca4-121">執行命令應該會將一個項目新增至您的專案檔，如下所示：</span><span class="sxs-lookup"><span data-stu-id="44ca4-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="44ca4-122">執行 `dotnet build` 建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="44ca4-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="44ca4-123">如果所有項目都成功，則會在輸出資料夾中產生名為 *MyWCFClient.XmlSerializers.dll* 的組件。</span><span class="sxs-lookup"><span data-stu-id="44ca4-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="44ca4-124">如果此工具無法產生組件，您將在建置輸出中看到警告。</span><span class="sxs-lookup"><span data-stu-id="44ca4-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="44ca4-125">啟動 WCF 服務，例如在瀏覽器中執行 `http://localhost:2561/Service1.svc`。</span><span class="sxs-lookup"><span data-stu-id="44ca4-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="44ca4-126">然後啟動用戶端應用程式，它將在執行階段自動載入和使用預先產生的序列化程式。</span><span class="sxs-lookup"><span data-stu-id="44ca4-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>