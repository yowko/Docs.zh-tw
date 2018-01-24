---
title: "在 .NET Core 上使用 Microsoft XML 序列化程式產生器"
description: "Microsoft XML 序列化程式產生器的概觀。"
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="cf234-103">在 .NET Core 上使用 Microsoft XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="cf234-103">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="cf234-104">本教學課程教導您如何在 C#.NET Core 應用程式中使用 Microsoft XML 序列化程式產生器。</span><span class="sxs-lookup"><span data-stu-id="cf234-104">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="cf234-105">您會在本教學課程中了解︰</span><span class="sxs-lookup"><span data-stu-id="cf234-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="cf234-106">如何建立 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="cf234-106">How to create a .NET Core app</span></span>
> * <span data-ttu-id="cf234-107">如何新增 Microsoft.XmlSerializer.Generator 套件的參考</span><span class="sxs-lookup"><span data-stu-id="cf234-107">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="cf234-108">如何編輯 MyApp.csproj 以新增相依性</span><span class="sxs-lookup"><span data-stu-id="cf234-108">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="cf234-109">如何新增類別和 XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="cf234-109">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="cf234-110">如何建置和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="cf234-110">How to build and run the application</span></span> 

<span data-ttu-id="cf234-111">[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [XML 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是 .NET Core 和 .NET Standard 專案的對等項目。</span><span class="sxs-lookup"><span data-stu-id="cf234-111">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="cf234-112">此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="cf234-112">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cf234-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="cf234-113">Prerequisites</span></span>

<span data-ttu-id="cf234-114">完成本教學課程：</span><span class="sxs-lookup"><span data-stu-id="cf234-114">To complete this tutorial:</span></span>

* <span data-ttu-id="cf234-115">安裝 [.NET Core SDK 2.1.3 或更新版本](https://www.microsoft.com/net/download)</span><span class="sxs-lookup"><span data-stu-id="cf234-115">Install [.NET Core SDK 2.1.3 or later](https://www.microsoft.com/net/download)</span></span>
* <span data-ttu-id="cf234-116">如果您還沒有這麼做，請安裝您慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="cf234-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="cf234-117">需要安裝程式碼編輯器嗎？</span><span class="sxs-lookup"><span data-stu-id="cf234-117">Need to install a code editor?</span></span> <span data-ttu-id="cf234-118">試用 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)！</span><span class="sxs-lookup"><span data-stu-id="cf234-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="cf234-119">在 .NET Core 主控台應用程式中使用 Microsoft XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="cf234-119">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="cf234-120">下列指示示範如何在 .NET Core 主控台應用程式中使用 XML 序列化程式產生器。</span><span class="sxs-lookup"><span data-stu-id="cf234-120">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="cf234-121">建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="cf234-121">Create a .NET Core console application</span></span>

<span data-ttu-id="cf234-122">開啟命令提示字元，並建立名為 *MyApp* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="cf234-122">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="cf234-123">巡覽至您已建立的資料夾，並鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="cf234-123">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="cf234-124">在 MyApp 專案中新增 Microsoft.XmlSerializer.Generator 套件的參考</span><span class="sxs-lookup"><span data-stu-id="cf234-124">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="cf234-125">使用 [`dotnet add package`](../tools//dotnet-add-package.md) 命令，在專案中新增參考。</span><span class="sxs-lookup"><span data-stu-id="cf234-125">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="cf234-126">類型：</span><span class="sxs-lookup"><span data-stu-id="cf234-126">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="cf234-127">在新增套件之後驗證 MyApp.csproj 變更</span><span class="sxs-lookup"><span data-stu-id="cf234-127">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="cf234-128">開啟程式碼編輯器，並讓我們開始吧！</span><span class="sxs-lookup"><span data-stu-id="cf234-128">Open your code editor and let's get started!</span></span> <span data-ttu-id="cf234-129">我們仍然從在其中建置應用程式的 *MyApp* 目錄中工作。</span><span class="sxs-lookup"><span data-stu-id="cf234-129">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="cf234-130">在文字編輯器中，開啟 *MyApp.csproj*。</span><span class="sxs-lookup"><span data-stu-id="cf234-130">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="cf234-131">執行 [`dotnet add package`](../tools//dotnet-add-package.md) 命令之後，會將下列數行新增至 *MyApp.csproj* 專案檔：</span><span class="sxs-lookup"><span data-stu-id="cf234-131">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="cf234-132">新增 .NET Core CLI 工具支援的另一個 ItemGroup 區段</span><span class="sxs-lookup"><span data-stu-id="cf234-132">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="cf234-133">在檢查的 `ItemGroup` 區段後面新增下列數行：</span><span class="sxs-lookup"><span data-stu-id="cf234-133">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="cf234-134">在應用程式中新增類別</span><span class="sxs-lookup"><span data-stu-id="cf234-134">Add a class in the application</span></span>

<span data-ttu-id="cf234-135">在文字編輯器中，開啟 *Program.cs*。</span><span class="sxs-lookup"><span data-stu-id="cf234-135">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="cf234-136">在 *Program.cs* 中，新增名為 *MyClass* 的類別。</span><span class="sxs-lookup"><span data-stu-id="cf234-136">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="cf234-137">建立 MyClass 的 `XmlSerializer`</span><span class="sxs-lookup"><span data-stu-id="cf234-137">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="cf234-138">在 *Main* 內新增下列數行，以建立 MyClass 的 `XmlSerializer`：</span><span class="sxs-lookup"><span data-stu-id="cf234-138">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="cf234-139">建立和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="cf234-139">Build and run the application</span></span>

<span data-ttu-id="cf234-140">在 *MyApp* 資料夾內，仍然透過 [`dotnet run`](../tools/dotnet-run.md) 執行應用程式，並在執行階段自動載入和使用預先產生的序列化程式。</span><span class="sxs-lookup"><span data-stu-id="cf234-140">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="cf234-141">在主控台視窗中，鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="cf234-141">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="cf234-142">[`dotnet run`](../tools/dotnet-run.md) 呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf234-142">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf234-143">本教學課程中所示用於執行應用程式的命令和步驟，僅供開發階段使用。</span><span class="sxs-lookup"><span data-stu-id="cf234-143">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="cf234-144">準備好部署應用程式之後，請查看不同的 .NET Core 應用程式[部署策略](../deploying/index.md)和 [`dotnet publish`](../tools/dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="cf234-144">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="cf234-145">如果所有項目都成功，則會在輸出資料夾中產生名為 *MyApp.XmlSerializers.dll* 的組件。</span><span class="sxs-lookup"><span data-stu-id="cf234-145">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="cf234-146">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="cf234-146">Congratulations!</span></span> <span data-ttu-id="cf234-147">您已：</span><span class="sxs-lookup"><span data-stu-id="cf234-147">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="cf234-148">建立 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf234-148">Created a .NET Core app.</span></span>
> * <span data-ttu-id="cf234-149">新增 Microsoft.XmlSerializer.Generator 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="cf234-149">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="cf234-150">編輯 MyApp.csproj 以新增相依性。</span><span class="sxs-lookup"><span data-stu-id="cf234-150">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="cf234-151">新增類別和 XmlSerializer。</span><span class="sxs-lookup"><span data-stu-id="cf234-151">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="cf234-152">建置和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf234-152">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="cf234-153">相關資源</span><span class="sxs-lookup"><span data-stu-id="cf234-153">Related Resources</span></span>

* [<span data-ttu-id="cf234-154">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="cf234-154">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="cf234-155">如何：使用 XmlSerializer 進行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="cf234-155">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)
* [<span data-ttu-id="cf234-156">如何：使用 XmlSerializer 進行序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf234-156">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)