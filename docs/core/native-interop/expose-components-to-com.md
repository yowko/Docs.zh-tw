---
title: 向 COM 公開 .NET 核心元件
description: 本教程演示如何從 .NET Core 向 COM 公開類。 為無註冊表的 COM 生成 COM 伺服器和並行伺服器清單。
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 98d303c99693a8aadb23da509a700772db69c0e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146654"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="d3e1b-104">向 COM 公開 .NET 核心元件</span><span class="sxs-lookup"><span data-stu-id="d3e1b-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="d3e1b-105">在 .NET Core 中，相較於 .NET Framework，向 COM 公開您 .NET 物件的流程已大幅簡化。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="d3e1b-106">下列流程將逐步解說如何向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="d3e1b-107">本教學課程說明如何：</span><span class="sxs-lookup"><span data-stu-id="d3e1b-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="d3e1b-108">從 .NET Core 向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="d3e1b-109">在建置您的 .NET Core 程式庫時，一併產生 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="d3e1b-110">自動為 Registry-Free COM 產生並存伺服器資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3e1b-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="d3e1b-111">Prerequisites</span></span>

- <span data-ttu-id="d3e1b-112">安裝[.NET 核心 3.0 SDK](https://dotnet.microsoft.com/download)或較新版本。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="d3e1b-113">建立程式庫</span><span class="sxs-lookup"><span data-stu-id="d3e1b-113">Create the library</span></span>

<span data-ttu-id="d3e1b-114">第一步是建立程式庫。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="d3e1b-115">創建新資料夾，該資料夾中運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d3e1b-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="d3e1b-116">開啟 `Class1.cs`。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="d3e1b-117">將 `using System.Runtime.InteropServices;` 新增到檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="d3e1b-118">建立名為 `IServer` 的介面。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="d3e1b-119">例如：</span><span class="sxs-lookup"><span data-stu-id="d3e1b-119">For example:</span></span>

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

5. <span data-ttu-id="d3e1b-120">使用您要實作之 COM 介面的介面 GUID，將 `[Guid("<IID>")]` 屬性新增到介面。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="d3e1b-121">例如： `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]` 。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="d3e1b-122">請注意，因為對 COM 而言，此 GUID 是此介面的唯一識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="d3e1b-123">在 Visual Studio 中，您可以前往 [工具] > [建立 GUID] 開啟建立 GUID 工具，以產生 GUID。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="d3e1b-124">將 `[InterfaceType]` 屬性新增到介面，並指定您介面應實作的基底 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="d3e1b-125">建立名為 `Server` 且實作 `IServer` 的類別。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="d3e1b-126">使用您要實作之 COM 類別的識別碼 GUID，將 `[Guid("<CLSID>")]` 屬性新增到類別。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="d3e1b-127">例如： `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]` 。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="d3e1b-128">一如介面 GUID，因為對 COM 而言，此 GUID 是此介面唯一的識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="d3e1b-129">將 `[ComVisible(true)]` 屬性新增到介面和類別。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3e1b-130">不同於 .NET Framework，.NET Core 會要求您為您希望可以透過 COM 啟動的所有類別指定 CLSID。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="d3e1b-131">產生 COM 主機</span><span class="sxs-lookup"><span data-stu-id="d3e1b-131">Generate the COM host</span></span>

1. <span data-ttu-id="d3e1b-132">開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableComHosting>true</EnableComHosting>`。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="d3e1b-133">建置專案。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-133">Build the project.</span></span>

<span data-ttu-id="d3e1b-134">產生的輸出包含 `ProjectName.dll`、`ProjectName.deps.json`、`ProjectName.runtimeconfig.json` 和 `ProjectName.comhost.dll` 檔案。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="d3e1b-135">為 COM 註冊 COM 主機</span><span class="sxs-lookup"><span data-stu-id="d3e1b-135">Register the COM host for COM</span></span>

<span data-ttu-id="d3e1b-136">開啟提升權限的命令提示字元，然後執行 `regsvr32 ProjectName.comhost.dll`。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="d3e1b-137">這會向 COM 註冊您所有的公開 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="d3e1b-138">啟用 RegFree COM</span><span class="sxs-lookup"><span data-stu-id="d3e1b-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="d3e1b-139">開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableRegFreeCom>true</EnableRegFreeCom>`。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="d3e1b-140">建置專案。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-140">Build the project.</span></span>

<span data-ttu-id="d3e1b-141">產生的輸出現在還包含 `ProjectName.X.manifest` 檔案。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="d3e1b-142">此檔案為並存資訊清單，可與 Registry-Free COM 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="d3e1b-143">範例</span><span class="sxs-lookup"><span data-stu-id="d3e1b-143">Sample</span></span>

<span data-ttu-id="d3e1b-144">GitHub 上的 dotnet/samples 存放庫提供功能完整的 [COM 伺服器範例](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="d3e1b-145">其他注意事項</span><span class="sxs-lookup"><span data-stu-id="d3e1b-145">Additional notes</span></span>

<span data-ttu-id="d3e1b-146">不同於 .NET Framework，.NET Core 不支援從 .NET Core 組件產生 COM 型別程式庫 (TLB)。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="d3e1b-147">該指南是手動編寫 COM 介面的本機聲明的 IDL 檔或 C/C++標頭。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="d3e1b-148">此外，將 .NET 框架和 .NET Core 載入到同一進程中確實具有診斷限制。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-148">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="d3e1b-149">主要限制是託管元件的調試，因為無法同時調試 .NET 框架和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-149">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="d3e1b-150">此外，兩個運行時實例不共用託管程式集。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-150">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="d3e1b-151">這意味著不可能在兩個運行時共用實際的 .NET 類型，相反，所有交互都必須限制為公開的 COM 介面協定。</span><span class="sxs-lookup"><span data-stu-id="d3e1b-151">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
