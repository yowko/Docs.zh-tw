---
title: 將 .NET Core 元件公開給 COM
description: 本教學課程說明如何從 .NET Core 向 COM 公開類別。 您可以針對免登錄的 COM 產生 COM 伺服器和並存伺服器資訊清單。
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 346776ebae3a6077fd39f26d5bd19d599d163db2
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608345"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="14196-104">將 .NET Core 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="14196-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="14196-105">在 .NET Core 中，相較於 .NET Framework，向 COM 公開您 .NET 物件的流程已大幅簡化。</span><span class="sxs-lookup"><span data-stu-id="14196-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="14196-106">下列流程將逐步解說如何向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="14196-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="14196-107">本教學課程說明如何：</span><span class="sxs-lookup"><span data-stu-id="14196-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="14196-108">從 .NET Core 向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="14196-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="14196-109">在建置您的 .NET Core 程式庫時，一併產生 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="14196-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="14196-110">自動為 Registry-Free COM 產生並存伺服器資訊清單。</span><span class="sxs-lookup"><span data-stu-id="14196-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14196-111">先決條件</span><span class="sxs-lookup"><span data-stu-id="14196-111">Prerequisites</span></span>

- <span data-ttu-id="14196-112">安裝 [.Net Core 3.0 SDK](https://dotnet.microsoft.com/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="14196-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="14196-113">建立程式庫</span><span class="sxs-lookup"><span data-stu-id="14196-113">Create the library</span></span>

<span data-ttu-id="14196-114">第一步是建立程式庫。</span><span class="sxs-lookup"><span data-stu-id="14196-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="14196-115">建立新的資料夾，然後在該資料夾中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="14196-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="14196-116">開啟 `Class1.cs`。</span><span class="sxs-lookup"><span data-stu-id="14196-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="14196-117">將 `using System.Runtime.InteropServices;` 新增到檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="14196-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="14196-118">建立名為 `IServer` 的介面。</span><span class="sxs-lookup"><span data-stu-id="14196-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="14196-119">例如：</span><span class="sxs-lookup"><span data-stu-id="14196-119">For example:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. <span data-ttu-id="14196-120">使用您要實作之 COM 介面的介面 GUID，將 `[Guid("<IID>")]` 屬性新增到介面。</span><span class="sxs-lookup"><span data-stu-id="14196-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="14196-121">例如： `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]` 。</span><span class="sxs-lookup"><span data-stu-id="14196-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="14196-122">請注意，因為對 COM 而言，此 GUID 是此介面的唯一識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="14196-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="14196-123">在 Visual Studio 中，您可以前往 [工具] > [建立 GUID] 開啟建立 GUID 工具，以產生 GUID。</span><span class="sxs-lookup"><span data-stu-id="14196-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="14196-124">將 `[InterfaceType]` 屬性新增到介面，並指定您介面應實作的基底 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="14196-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="14196-125">建立名為 `Server` 且實作 `IServer` 的類別。</span><span class="sxs-lookup"><span data-stu-id="14196-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="14196-126">使用您要實作之 COM 類別的識別碼 GUID，將 `[Guid("<CLSID>")]` 屬性新增到類別。</span><span class="sxs-lookup"><span data-stu-id="14196-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="14196-127">例如： `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]` 。</span><span class="sxs-lookup"><span data-stu-id="14196-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="14196-128">一如介面 GUID，因為對 COM 而言，此 GUID 是此介面唯一的識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="14196-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="14196-129">將 `[ComVisible(true)]` 屬性新增到介面和類別。</span><span class="sxs-lookup"><span data-stu-id="14196-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14196-130">不同於 .NET Framework，.NET Core 會要求您為您希望可以透過 COM 啟動的所有類別指定 CLSID。</span><span class="sxs-lookup"><span data-stu-id="14196-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="14196-131">產生 COM 主機</span><span class="sxs-lookup"><span data-stu-id="14196-131">Generate the COM host</span></span>

1. <span data-ttu-id="14196-132">開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableComHosting>true</EnableComHosting>`。</span><span class="sxs-lookup"><span data-stu-id="14196-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="14196-133">建置專案。</span><span class="sxs-lookup"><span data-stu-id="14196-133">Build the project.</span></span>

<span data-ttu-id="14196-134">產生的輸出包含 `ProjectName.dll`、`ProjectName.deps.json`、`ProjectName.runtimeconfig.json` 和 `ProjectName.comhost.dll` 檔案。</span><span class="sxs-lookup"><span data-stu-id="14196-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="14196-135">為 COM 註冊 COM 主機</span><span class="sxs-lookup"><span data-stu-id="14196-135">Register the COM host for COM</span></span>

<span data-ttu-id="14196-136">開啟提升權限的命令提示字元，然後執行 `regsvr32 ProjectName.comhost.dll`。</span><span class="sxs-lookup"><span data-stu-id="14196-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="14196-137">這會向 COM 註冊您所有的公開 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="14196-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="14196-138">啟用 RegFree COM</span><span class="sxs-lookup"><span data-stu-id="14196-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="14196-139">開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableRegFreeCom>true</EnableRegFreeCom>`。</span><span class="sxs-lookup"><span data-stu-id="14196-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="14196-140">建置專案。</span><span class="sxs-lookup"><span data-stu-id="14196-140">Build the project.</span></span>

<span data-ttu-id="14196-141">產生的輸出現在還包含 `ProjectName.X.manifest` 檔案。</span><span class="sxs-lookup"><span data-stu-id="14196-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="14196-142">此檔案為並存資訊清單，可與 Registry-Free COM 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="14196-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="14196-143">範例</span><span class="sxs-lookup"><span data-stu-id="14196-143">Sample</span></span>

<span data-ttu-id="14196-144">GitHub 上的 dotnet/samples 存放庫提供功能完整的 [COM 伺服器範例](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)。</span><span class="sxs-lookup"><span data-stu-id="14196-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="14196-145">其他注意事項</span><span class="sxs-lookup"><span data-stu-id="14196-145">Additional notes</span></span>

<span data-ttu-id="14196-146">不同於 .NET Framework，.NET Core 不支援從 .NET Core 組件產生 COM 型別程式庫 (TLB)。</span><span class="sxs-lookup"><span data-stu-id="14196-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="14196-147">本指引是針對 COM 介面的原生宣告，手動寫入 IDL 檔案或 C/c + + 標頭。</span><span class="sxs-lookup"><span data-stu-id="14196-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="14196-148">不支援 COM 元件的[獨立部署](../deploying/index.md#publish-self-contained)。</span><span class="sxs-lookup"><span data-stu-id="14196-148">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="14196-149">僅支援與 [framework 相依](../deploying/index.md#publish-framework-dependent) 的 COM 元件部署。</span><span class="sxs-lookup"><span data-stu-id="14196-149">Only [framework-dependent deployments](../deploying/index.md#publish-framework-dependent) of COM components are supported.</span></span>

<span data-ttu-id="14196-150">此外，將 .NET Framework 和 .NET Core 載入至相同的進程有診斷限制。</span><span class="sxs-lookup"><span data-stu-id="14196-150">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="14196-151">主要限制是 managed 元件的偵錯工具，因為無法同時同時進行 .NET Framework 和 .NET Core 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="14196-151">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="14196-152">此外，兩個執行時間實例不會共用 managed 元件。</span><span class="sxs-lookup"><span data-stu-id="14196-152">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="14196-153">這表示，您無法在兩個執行時間之間共用實際的 .NET 型別，而是必須將所有互動限制為公開的 COM 介面合約。</span><span class="sxs-lookup"><span data-stu-id="14196-153">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
