---
title: 將 .NET 核心元件公開給 COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 33574eeac5b1f7aa2067b1974f3f2e68fb22e8ff
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577170"
---
# <a name="exposing-net-core-components-to-com"></a>將 .NET 核心元件公開給 COM

在 .NET Core 中，相較於 .NET Framework，向 COM 公開您 .NET 物件的流程已大幅簡化。 下列流程將逐步解說如何向 COM 公開類別。 本教學課程會示範如何：

- 從 .NET Core 向 COM 公開類別。
- 在建置您的 .NET Core 程式庫時，一併產生 COM 伺服器。
- 自動為 Registry-Free COM 產生並存伺服器資訊清單。

## <a name="prerequisites"></a>必要條件

- 安裝 [.NET Core 3.0 Preview 7 SDK](https://www.microsoft.com/net/core) 或更新版本。

## <a name="create-the-library"></a>建立程式庫

第一步是建立程式庫。

1. 建立新的資料夾，並在該資料夾中執行 `dotnet new classlib`。
2. 開啟 `Class1.cs`。
3. 將 `using System.Runtime.InteropServices;` 新增到檔案的頂端。
4. 建立名為 `IServer` 的介面。 例如：[!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]
5. 使用您要實作之 COM 介面的介面 GUID，將 `[Guid("<IID>")]` 屬性新增到介面。 例如，`[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`。 請注意，因為對 COM 而言，此 GUID 是此介面的唯一識別碼，所以其必須是唯一的。 在 Visual Studio 中，您可以前往 [工具] > [建立 GUID] 開啟建立 GUID 工具，以產生 GUID。
6. 將 `[InterfaceType]` 屬性新增到介面，並指定您介面應實作的基底 COM 介面。
7. 建立名為 `Server` 且實作 `IServer` 的類別。
8. 使用您要實作之 COM 類別的識別碼 GUID，將 `[Guid("<CLSID>")]` 屬性新增到類別。 例如，`[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`。 一如介面 GUID，因為對 COM 而言，此 GUID 是此介面唯一的識別碼，所以其必須是唯一的。
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

不同於 .NET Framework，.NET Core 不支援從 .NET Core 組件產生 COM 型別程式庫 (TLB)。 您必須手動撰寫 IDL 檔案，或為您介面的原生宣告撰寫 C++ 標頭。

此外，因為不支援將 .NET Framework 和 .NET Core 載入同一個處理序，所以支援將 .NET Core COM 伺服器載入 .NET Framework COM 用戶端處理序 (反之亦然)。
