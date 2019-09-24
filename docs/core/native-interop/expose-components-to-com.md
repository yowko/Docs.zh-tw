---
title: 將 .NET Core 元件公開給 COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 8f9624414a2b423bd43e8790d11b70ae1ca6286d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216235"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="a6a0c-102">將 .NET Core 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="a6a0c-102">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="a6a0c-103">在 .NET Core 中，相較於 .NET Framework，向 COM 公開您 .NET 物件的流程已大幅簡化。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="a6a0c-104">下列流程將逐步解說如何向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="a6a0c-105">本教學課程會示範如何：</span><span class="sxs-lookup"><span data-stu-id="a6a0c-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="a6a0c-106">從 .NET Core 向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="a6a0c-107">在建置您的 .NET Core 程式庫時，一併產生 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="a6a0c-108">自動為 Registry-Free COM 產生並存伺服器資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a6a0c-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="a6a0c-109">Prerequisites</span></span>

- <span data-ttu-id="a6a0c-110">安裝[.Net Core 3.0 SDK](https://dotnet.microsoft.com/download)或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-110">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="a6a0c-111">建立程式庫</span><span class="sxs-lookup"><span data-stu-id="a6a0c-111">Create the library</span></span>

<span data-ttu-id="a6a0c-112">第一步是建立程式庫。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="a6a0c-113">建立新的資料夾，然後在該資料夾中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a6a0c-113">Create a new folder, and in that folder run the following command:</span></span>
    
    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="a6a0c-114">開啟 `Class1.cs`。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="a6a0c-115">將 `using System.Runtime.InteropServices;` 新增到檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="a6a0c-116">建立名為 `IServer` 的介面。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="a6a0c-117">例如：</span><span class="sxs-lookup"><span data-stu-id="a6a0c-117">For example:</span></span>

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. <span data-ttu-id="a6a0c-118">使用您要實作之 COM 介面的介面 GUID，將 `[Guid("<IID>")]` 屬性新增到介面。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="a6a0c-119">例如，`[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="a6a0c-120">請注意，因為對 COM 而言，此 GUID 是此介面的唯一識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="a6a0c-121">在 Visual Studio 中，您可以前往 [工具] > [建立 GUID] 開啟建立 GUID 工具，以產生 GUID。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="a6a0c-122">將 `[InterfaceType]` 屬性新增到介面，並指定您介面應實作的基底 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="a6a0c-123">建立名為 `Server` 且實作 `IServer` 的類別。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="a6a0c-124">使用您要實作之 COM 類別的識別碼 GUID，將 `[Guid("<CLSID>")]` 屬性新增到類別。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="a6a0c-125">例如，`[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="a6a0c-126">一如介面 GUID，因為對 COM 而言，此 GUID 是此介面唯一的識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="a6a0c-127">將 `[ComVisible(true)]` 屬性新增到介面和類別。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6a0c-128">不同於 .NET Framework，.NET Core 會要求您為您希望可以透過 COM 啟動的所有類別指定 CLSID。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="a6a0c-129">產生 COM 主機</span><span class="sxs-lookup"><span data-stu-id="a6a0c-129">Generate the COM host</span></span>

1. <span data-ttu-id="a6a0c-130">開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableComHosting>true</EnableComHosting>`。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="a6a0c-131">建置專案。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-131">Build the project.</span></span>

<span data-ttu-id="a6a0c-132">產生的輸出包含 `ProjectName.dll`、`ProjectName.deps.json`、`ProjectName.runtimeconfig.json` 和 `ProjectName.comhost.dll` 檔案。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="a6a0c-133">為 COM 註冊 COM 主機</span><span class="sxs-lookup"><span data-stu-id="a6a0c-133">Register the COM host for COM</span></span>

<span data-ttu-id="a6a0c-134">開啟提升權限的命令提示字元，然後執行 `regsvr32 ProjectName.comhost.dll`。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="a6a0c-135">這會向 COM 註冊您所有的公開 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="a6a0c-136">啟用 RegFree COM</span><span class="sxs-lookup"><span data-stu-id="a6a0c-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="a6a0c-137">開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableRegFreeCom>true</EnableRegFreeCom>`。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="a6a0c-138">建置專案。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-138">Build the project.</span></span>

<span data-ttu-id="a6a0c-139">產生的輸出現在還包含 `ProjectName.X.manifest` 檔案。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="a6a0c-140">此檔案為並存資訊清單，可與 Registry-Free COM 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="a6a0c-141">範例</span><span class="sxs-lookup"><span data-stu-id="a6a0c-141">Sample</span></span>

<span data-ttu-id="a6a0c-142">GitHub 上的 dotnet/samples 存放庫提供功能完整的 [COM 伺服器範例](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="a6a0c-143">其他備註</span><span class="sxs-lookup"><span data-stu-id="a6a0c-143">Additional notes</span></span>

<span data-ttu-id="a6a0c-144">不同於 .NET Framework，.NET Core 不支援從 .NET Core 組件產生 COM 型別程式庫 (TLB)。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="a6a0c-145">您必須手動撰寫 IDL 檔案，或為您介面的原生宣告撰寫 C++ 標頭。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-145">You will either have to manually write an IDL file or a C++ header for the native declarations of your interfaces.</span></span>

<span data-ttu-id="a6a0c-146">此外，因為不支援將 .NET Framework 和 .NET Core 載入同一個處理序，所以支援將 .NET Core COM 伺服器載入 .NET Framework COM 用戶端處理序 (反之亦然)。</span><span class="sxs-lookup"><span data-stu-id="a6a0c-146">Additionally, loading both .NET Framework and .NET Core into the same process is unsupported, and as a result loading a .NET Core COM server into a .NET Framework COM client process or vice versa is not supported.</span></span>
