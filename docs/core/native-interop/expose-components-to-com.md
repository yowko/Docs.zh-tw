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
ms.openlocfilehash: f6665e18e51af96761941e419fabc409e4b9391d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240970"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="28a7e-102">將 .NET Core 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="28a7e-102">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="28a7e-103">在 .NET Core 中，相較於 .NET Framework，向 COM 公開您 .NET 物件的流程已大幅簡化。</span><span class="sxs-lookup"><span data-stu-id="28a7e-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="28a7e-104">下列流程將逐步解說如何向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="28a7e-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="28a7e-105">本教學課程說明如何：</span><span class="sxs-lookup"><span data-stu-id="28a7e-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="28a7e-106">從 .NET Core 向 COM 公開類別。</span><span class="sxs-lookup"><span data-stu-id="28a7e-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="28a7e-107">在建置您的 .NET Core 程式庫時，一併產生 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="28a7e-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="28a7e-108">自動為 Registry-Free COM 產生並存伺服器資訊清單。</span><span class="sxs-lookup"><span data-stu-id="28a7e-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28a7e-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="28a7e-109">Prerequisites</span></span>

- <span data-ttu-id="28a7e-110">安裝[.Net Core 3.0 SDK](https://dotnet.microsoft.com/download)或更新版本。</span><span class="sxs-lookup"><span data-stu-id="28a7e-110">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="28a7e-111">建立程式庫</span><span class="sxs-lookup"><span data-stu-id="28a7e-111">Create the library</span></span>

<span data-ttu-id="28a7e-112">第一步是建立程式庫。</span><span class="sxs-lookup"><span data-stu-id="28a7e-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="28a7e-113">建立新的資料夾，然後在該資料夾中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="28a7e-113">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="28a7e-114">開啟 `Class1.cs`。</span><span class="sxs-lookup"><span data-stu-id="28a7e-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="28a7e-115">將 `using System.Runtime.InteropServices;` 新增到檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="28a7e-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="28a7e-116">建立名為 `IServer` 的介面。</span><span class="sxs-lookup"><span data-stu-id="28a7e-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="28a7e-117">例如：</span><span class="sxs-lookup"><span data-stu-id="28a7e-117">For example:</span></span>

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

5. <span data-ttu-id="28a7e-118">使用您要實作之 COM 介面的介面 GUID，將 `[Guid("<IID>")]` 屬性新增到介面。</span><span class="sxs-lookup"><span data-stu-id="28a7e-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="28a7e-119">例如： `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]` 。</span><span class="sxs-lookup"><span data-stu-id="28a7e-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="28a7e-120">請注意，因為對 COM 而言，此 GUID 是此介面的唯一識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="28a7e-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="28a7e-121">在 Visual Studio 中，您可以前往 [工具] > [建立 GUID] 開啟建立 GUID 工具，以產生 GUID。</span><span class="sxs-lookup"><span data-stu-id="28a7e-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="28a7e-122">將 `[InterfaceType]` 屬性新增到介面，並指定您介面應實作的基底 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="28a7e-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="28a7e-123">建立名為 `Server` 且實作 `IServer` 的類別。</span><span class="sxs-lookup"><span data-stu-id="28a7e-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="28a7e-124">使用您要實作之 COM 類別的識別碼 GUID，將 `[Guid("<CLSID>")]` 屬性新增到類別。</span><span class="sxs-lookup"><span data-stu-id="28a7e-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="28a7e-125">例如： `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]` 。</span><span class="sxs-lookup"><span data-stu-id="28a7e-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="28a7e-126">一如介面 GUID，因為對 COM 而言，此 GUID 是此介面唯一的識別碼，所以其必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="28a7e-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="28a7e-127">將 `[ComVisible(true)]` 屬性新增到介面和類別。</span><span class="sxs-lookup"><span data-stu-id="28a7e-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="28a7e-128">不同於 .NET Framework，.NET Core 會要求您為您希望可以透過 COM 啟動的所有類別指定 CLSID。</span><span class="sxs-lookup"><span data-stu-id="28a7e-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="28a7e-129">產生 COM 主機</span><span class="sxs-lookup"><span data-stu-id="28a7e-129">Generate the COM host</span></span>

1. <span data-ttu-id="28a7e-130">開啟 `.csproj` 專案檔，然後在 `<EnableComHosting>true</EnableComHosting>` 標籤內新增 `<PropertyGroup></PropertyGroup>`。</span><span class="sxs-lookup"><span data-stu-id="28a7e-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="28a7e-131">建置專案。</span><span class="sxs-lookup"><span data-stu-id="28a7e-131">Build the project.</span></span>

<span data-ttu-id="28a7e-132">產生的輸出包含 `ProjectName.dll`、`ProjectName.deps.json`、`ProjectName.runtimeconfig.json` 和 `ProjectName.comhost.dll` 檔案。</span><span class="sxs-lookup"><span data-stu-id="28a7e-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="28a7e-133">為 COM 註冊 COM 主機</span><span class="sxs-lookup"><span data-stu-id="28a7e-133">Register the COM host for COM</span></span>

<span data-ttu-id="28a7e-134">開啟提升權限的命令提示字元，然後執行 `regsvr32 ProjectName.comhost.dll`。</span><span class="sxs-lookup"><span data-stu-id="28a7e-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="28a7e-135">這會向 COM 註冊您所有的公開 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="28a7e-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="28a7e-136">啟用 RegFree COM</span><span class="sxs-lookup"><span data-stu-id="28a7e-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="28a7e-137">開啟 `.csproj` 專案檔，然後在 `<EnableRegFreeCom>true</EnableRegFreeCom>` 標籤內新增 `<PropertyGroup></PropertyGroup>`。</span><span class="sxs-lookup"><span data-stu-id="28a7e-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="28a7e-138">建置專案。</span><span class="sxs-lookup"><span data-stu-id="28a7e-138">Build the project.</span></span>

<span data-ttu-id="28a7e-139">產生的輸出現在還包含 `ProjectName.X.manifest` 檔案。</span><span class="sxs-lookup"><span data-stu-id="28a7e-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="28a7e-140">此檔案為並存資訊清單，可與 Registry-Free COM 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="28a7e-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="28a7e-141">範例</span><span class="sxs-lookup"><span data-stu-id="28a7e-141">Sample</span></span>

<span data-ttu-id="28a7e-142">GitHub 上的 dotnet/samples 存放庫提供功能完整的 [COM 伺服器範例](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)。</span><span class="sxs-lookup"><span data-stu-id="28a7e-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="28a7e-143">其他注意事項</span><span class="sxs-lookup"><span data-stu-id="28a7e-143">Additional notes</span></span>

<span data-ttu-id="28a7e-144">不同於 .NET Framework，.NET Core 不支援從 .NET Core 組件產生 COM 型別程式庫 (TLB)。</span><span class="sxs-lookup"><span data-stu-id="28a7e-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="28a7e-145">本指南是針對 COM 介面的原生宣告，手動撰寫 IDLC++檔案或 C/標頭。</span><span class="sxs-lookup"><span data-stu-id="28a7e-145">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="28a7e-146">此外，將 .NET Framework 和 .NET Core 載入相同的進程中，都有診斷限制。</span><span class="sxs-lookup"><span data-stu-id="28a7e-146">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="28a7e-147">主要的限制是 managed 元件的調試，因為無法同時進行 .NET Framework 和 .NET Core 的同時調試。</span><span class="sxs-lookup"><span data-stu-id="28a7e-147">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="28a7e-148">此外，這兩個執行時間實例不會共用 managed 元件。</span><span class="sxs-lookup"><span data-stu-id="28a7e-148">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="28a7e-149">這表示您無法在兩個執行時間之間共用實際的 .NET 類型，而是必須將所有互動限制為公開的 COM 介面合約。</span><span class="sxs-lookup"><span data-stu-id="28a7e-149">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
