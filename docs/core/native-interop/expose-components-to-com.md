---
title: Com 公開 .NET 核心元件
description: 本教程演示如何從 .NET Core 向 COM 公開類。 為無註冊表的 COM 生成 COM 伺服器和並行伺服器清單。
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 17d85b9e9734fae0bb69f94da8c08669216ab0ae
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242864"
---
# <a name="exposing-net-core-components-to-com"></a>Com 公開 .NET 核心元件

在 .NET Core 中，相較於 .NET Framework，向 COM 公開您 .NET 物件的流程已大幅簡化。 下列流程將逐步解說如何向 COM 公開類別。 本教學課程說明如何：

- 從 .NET Core 向 COM 公開類別。
- 在建置您的 .NET Core 程式庫時，一併產生 COM 伺服器。
- 自動為 Registry-Free COM 產生並存伺服器資訊清單。

## <a name="prerequisites"></a>Prerequisites

- 安裝[.NET 核心 3.0 SDK](https://dotnet.microsoft.com/download)或較新版本。

## <a name="create-the-library"></a>建立程式庫

第一步是建立程式庫。

1. 建立新資料夾,該資料夾中執行以下指令:

    ```dotnetcli
    dotnet new classlib
    ```

2. 開啟 `Class1.cs`。
3. 將 `using System.Runtime.InteropServices;` 新增到檔案的頂端。
4. 建立名為 `IServer` 的介面。 例如：

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

5. 使用您要實作之 COM 介面的介面 GUID，將 `[Guid("<IID>")]` 屬性新增到介面。 例如： `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]` 。 請注意，因為對 COM 而言，此 GUID 是此介面的唯一識別碼，所以其必須是唯一的。 在 Visual Studio 中，您可以前往 [工具] > [建立 GUID] 開啟建立 GUID 工具，以產生 GUID。
6. 將 `[InterfaceType]` 屬性新增到介面，並指定您介面應實作的基底 COM 介面。
7. 建立名為 `Server` 且實作 `IServer` 的類別。
8. 使用您要實作之 COM 類別的識別碼 GUID，將 `[Guid("<CLSID>")]` 屬性新增到類別。 例如： `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]` 。 一如介面 GUID，因為對 COM 而言，此 GUID 是此介面唯一的識別碼，所以其必須是唯一的。
9. 將 `[ComVisible(true)]` 屬性新增到介面和類別。

> [!IMPORTANT]
> 不同於 .NET Framework，.NET Core 會要求您為您希望可以透過 COM 啟動的所有類別指定 CLSID。

## <a name="generate-the-com-host"></a>產生 COM 主機

1. 開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableComHosting>true</EnableComHosting>`。
2. 建置專案。

產生的輸出包含 `ProjectName.dll`、`ProjectName.deps.json`、`ProjectName.runtimeconfig.json` 和 `ProjectName.comhost.dll` 檔案。

## <a name="register-the-com-host-for-com"></a>為 COM 註冊 COM 主機

開啟提升權限的命令提示字元，然後執行 `regsvr32 ProjectName.comhost.dll`。 這會向 COM 註冊您所有的公開 .NET 物件。

## <a name="enabling-regfree-com"></a>啟用 RegFree COM

1. 開啟 `.csproj` 專案檔，然後在 `<PropertyGroup></PropertyGroup>` 標籤內新增 `<EnableRegFreeCom>true</EnableRegFreeCom>`。
2. 建置專案。

產生的輸出現在還包含 `ProjectName.X.manifest` 檔案。 此檔案為並存資訊清單，可與 Registry-Free COM 搭配使用。

## <a name="sample"></a>範例

GitHub 上的 dotnet/samples 存放庫提供功能完整的 [COM 伺服器範例](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)。

## <a name="additional-notes"></a>其他注意事項

不同於 .NET Framework，.NET Core 不支援從 .NET Core 組件產生 COM 型別程式庫 (TLB)。 該指南是手動編寫 COM 介面的本機聲明的 IDL 檔或 C/C++標頭。

不支援[自包含](../deploying/index.md#publish-self-contained)的 COM 元件部署。 只支援 COM 元件[執行時相關部署](../deploying/index.md#publish-runtime-dependent)。

此外,將 .NET框架和 .NET Core 載入到同一進程中確實具有診斷限制。 主要限制是託管元件的調試,因為無法同時調試 .NET 框架和 .NET Core。 此外,兩個運行時實例不共用託管程式集。 這意味著不可能在兩個運行時共用實際的 .NET 類型,相反,所有交互都必須限制為公開的 COM 介面協定。
