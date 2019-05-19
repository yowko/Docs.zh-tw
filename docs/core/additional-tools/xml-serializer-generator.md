---
title: Microsoft XML 序列化程式產生器
description: Microsoft XML 序列化程式產生器的概觀。 您可以使用 XML 序列化程式產生器，為專案中包含的類型產生 XML 序列化組件。
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 74d10b0fb27a4acf477fc66451a5cf6fc1f4317c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631698"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="c8fe0-104">在 .NET Core 上使用 Microsoft XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="c8fe0-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="c8fe0-105">本教學課程教導您如何在 C#.NET Core 應用程式中使用 Microsoft XML 序列化程式產生器。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="c8fe0-106">您會在本教學課程中了解︰</span><span class="sxs-lookup"><span data-stu-id="c8fe0-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="c8fe0-107">如何建立 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="c8fe0-107">How to create a .NET Core app</span></span>
> * <span data-ttu-id="c8fe0-108">如何新增 Microsoft.XmlSerializer.Generator 套件的參考</span><span class="sxs-lookup"><span data-stu-id="c8fe0-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="c8fe0-109">如何編輯 MyApp.csproj 以新增相依性</span><span class="sxs-lookup"><span data-stu-id="c8fe0-109">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="c8fe0-110">如何新增類別和 XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="c8fe0-110">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="c8fe0-111">如何建置和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c8fe0-111">How to build and run the application</span></span>

<span data-ttu-id="c8fe0-112">[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [XML 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是 .NET Core 和 .NET Standard 專案的對等項目。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="c8fe0-113">此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8fe0-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="c8fe0-114">Prerequisites</span></span>

<span data-ttu-id="c8fe0-115">完成本教學課程：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-115">To complete this tutorial:</span></span>

* <span data-ttu-id="c8fe0-116">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c8fe0-116">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="c8fe0-117">您慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="c8fe0-118">需要安裝程式碼編輯器嗎？</span><span class="sxs-lookup"><span data-stu-id="c8fe0-118">Need to install a code editor?</span></span> <span data-ttu-id="c8fe0-119">試用 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)！</span><span class="sxs-lookup"><span data-stu-id="c8fe0-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="c8fe0-120">在 .NET Core 主控台應用程式中使用 Microsoft XML 序列化程式產生器</span><span class="sxs-lookup"><span data-stu-id="c8fe0-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="c8fe0-121">下列指示示範如何在 .NET Core 主控台應用程式中使用 XML 序列化程式產生器。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="c8fe0-122">建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c8fe0-122">Create a .NET Core console application</span></span>

<span data-ttu-id="c8fe0-123">開啟命令提示字元，並建立名為 *MyApp* 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="c8fe0-124">巡覽至您已建立的資料夾，並鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-124">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="c8fe0-125">在 MyApp 專案中新增 Microsoft.XmlSerializer.Generator 套件的參考</span><span class="sxs-lookup"><span data-stu-id="c8fe0-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="c8fe0-126">使用 [`dotnet add package`](../tools//dotnet-add-package.md) 命令，在專案中新增參考。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="c8fe0-127">類型：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-127">Type:</span></span>

```console
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="c8fe0-128">在新增套件之後驗證 MyApp.csproj 變更</span><span class="sxs-lookup"><span data-stu-id="c8fe0-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="c8fe0-129">開啟程式碼編輯器，並讓我們開始吧！</span><span class="sxs-lookup"><span data-stu-id="c8fe0-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="c8fe0-130">我們仍然從在其中建置應用程式的 *MyApp* 目錄中工作。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="c8fe0-131">在文字編輯器中，開啟 *MyApp.csproj*。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="c8fe0-132">執行 [`dotnet add package`](../tools//dotnet-add-package.md) 命令之後，會將下列數行新增至 *MyApp.csproj* 專案檔：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="c8fe0-133">新增 .NET Core CLI 工具支援的另一個 ItemGroup 區段</span><span class="sxs-lookup"><span data-stu-id="c8fe0-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="c8fe0-134">在檢查的 `ItemGroup` 區段後面新增下列數行：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="c8fe0-135">在應用程式中新增類別</span><span class="sxs-lookup"><span data-stu-id="c8fe0-135">Add a class in the application</span></span>

<span data-ttu-id="c8fe0-136">在文字編輯器中，開啟 *Program.cs*。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="c8fe0-137">在 *Program.cs* 中，新增名為 *MyClass* 的類別。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="c8fe0-138">建立 MyClass 的 `XmlSerializer`</span><span class="sxs-lookup"><span data-stu-id="c8fe0-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="c8fe0-139">在 *Main* 內新增下列數行，以建立 MyClass 的 `XmlSerializer`：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="c8fe0-140">建立和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c8fe0-140">Build and run the application</span></span>

<span data-ttu-id="c8fe0-141">在 *MyApp* 資料夾內，仍然透過 [`dotnet run`](../tools/dotnet-run.md) 執行應用程式，並在執行階段自動載入和使用預先產生的序列化程式。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="c8fe0-142">在主控台視窗中，鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-142">Type the following command in your console window:</span></span>

```console
dotnet run
```

> [!NOTE]
> <span data-ttu-id="c8fe0-143">[`dotnet run`](../tools/dotnet-run.md) 呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8fe0-144">本教學課程中所示用於執行應用程式的命令和步驟，僅供開發階段使用。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="c8fe0-145">準備好部署應用程式之後，請查看不同的 .NET Core 應用程式[部署策略](../deploying/index.md)和 [`dotnet publish`](../tools/dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="c8fe0-146">如果所有項目都成功，則會在輸出資料夾中產生名為 *MyApp.XmlSerializers.dll* 的組件。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="c8fe0-147">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="c8fe0-147">Congratulations!</span></span> <span data-ttu-id="c8fe0-148">您已：</span><span class="sxs-lookup"><span data-stu-id="c8fe0-148">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c8fe0-149">建立 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-149">Created a .NET Core app.</span></span>
> * <span data-ttu-id="c8fe0-150">新增 Microsoft.XmlSerializer.Generator 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="c8fe0-151">編輯 MyApp.csproj 以新增相依性。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-151">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="c8fe0-152">新增類別和 XmlSerializer。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-152">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="c8fe0-153">建置和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8fe0-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="c8fe0-154">相關資源</span><span class="sxs-lookup"><span data-stu-id="c8fe0-154">Related resources</span></span>

* [<span data-ttu-id="c8fe0-155">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="c8fe0-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="c8fe0-156">如何：使用 XmlSerializer 進行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="c8fe0-156">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [<span data-ttu-id="c8fe0-157">如何：使用 XmlSerializer 進行序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8fe0-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
