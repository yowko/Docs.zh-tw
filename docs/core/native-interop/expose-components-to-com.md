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
# <a name="exposing-net-core-components-to-com"></a>將 .NET Core 元件公開給 COM

在 .NET Core 中，相較於 .NET Framework，向 COM 公開您 .NET 物件的流程已大幅簡化。 下列流程將逐步解說如何向 COM 公開類別。 本教學課程說明如何：

- 從 .NET Core 向 COM 公開類別。
- 在建置您的 .NET Core 程式庫時，一併產生 COM 伺服器。
- 自動為 Registry-Free COM 產生並存伺服器資訊清單。

## <a name="prerequisites"></a>先決條件

- 安裝 [.Net Core 3.0 SDK](https://dotnet.microsoft.com/download) 或更新版本。

## <a name="create-the-library"></a>建立程式庫

第一步是建立程式庫。

1. 建立新的資料夾，然後在該資料夾中執行下列命令：

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

不同於 .NET Framework，.NET Core 不支援從 .NET Core 組件產生 COM 型別程式庫 (TLB)。 本指引是針對 COM 介面的原生宣告，手動寫入 IDL 檔案或 C/c + + 標頭。

不支援 COM 元件的[獨立部署](../deploying/index.md#publish-self-contained)。 僅支援與 [framework 相依](../deploying/index.md#publish-framework-dependent) 的 COM 元件部署。

此外，將 .NET Framework 和 .NET Core 載入至相同的進程有診斷限制。 主要限制是 managed 元件的偵錯工具，因為無法同時同時進行 .NET Framework 和 .NET Core 的偵錯工具。 此外，兩個執行時間實例不會共用 managed 元件。 這表示，您無法在兩個執行時間之間共用實際的 .NET 型別，而是必須將所有互動限制為公開的 COM 介面合約。
