---
title: .NET 架構和 .NET 核心之間的差異
description: 描述 Windows 示範基礎 (WPF) 的 .NET 框架實現和 .NET 核心 WPF 之間的差異。 遷移應用時,應考慮這些不相容因素。
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072204"
---
# <a name="differences-in-wpf"></a>WPF 的差異

本文介紹了 .NET 核心和 .NET 框架上的 Windows 演示基礎 (WPF) 之間的差異。 .NET Core 的 WPF 是從原始 WPF 為 .NET 框架原始程式碼分叉的[開源框架](https://github.com/dotnet/wpf)。

.NET 框架有幾個功能,而 .NET Core 不支援這些功能。 有關不支援的技術的詳細資訊,請參閱[.NET 框架技術在 .NET Core 上不可用](../../core/porting/net-framework-tech-unavailable.md)。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>SDK 風格的項目

.NET Core 使用 SDK 風格的專案檔。 這些專案檔不同於 Visual Studio 管理的傳統 .NET 框架專案檔。 要將 .NET 框架 WPF 應用遷移到 .NET Core,必須轉換專案。 有關詳細資訊,請參閱將[WPF 應用遷移到 .NET 核心 3.0](convert-project-from-net-framework.md)。

## <a name="nuget-package-references"></a>NuGet 封裝參考

如果您的 .NET Framework 應用在套件中列出了其 NuGet 相依項 *。* [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)

1. 在可視化工作室中,打開 **「解決方案資源管理器」** 窗格。
1. 在 WPF 專案中,右鍵按下**套件.config** > **移轉包。config 到套件參考**。

![升級到包參考](media/differences-from-net-framework/package-reference-migration.png)

將顯示一個對話框,顯示計算的頂級 NuGet 依賴項,並詢問應將哪些其他 NuGet 包提升到頂層。 選擇 **「 確定**」*套件.config*檔將從項目中`<PackageReference>`刪除, 元素將新增到專案檔中。

當專案使用`<PackageReference>`時,包不會存儲在 *「包」* 資料夾中本地,它們存儲在全域。 開啟專案檔並刪除參考`<Analyzer>`*「包」* 資料夾的任何元素。 這些分析器會自動包含在 NuGet 包引用中。

## <a name="code-access-security"></a>程式碼存取安全性

.NET 核心或 .NET Core 的 WPF 不支援代碼存取安全性 (CAS)。 所有 CAS 相關功能均以完全信任為假設處理。 .NET Core 的 WPF 刪除 CAS 相關代碼。 這些類型的公共 API 表面仍然存在,以確保對這些類型的調用成功。

公開定義的 CAS 相關類型從 WPF 程式集移出並移動到 Core .NET 庫程式集中。 WPF 程式集具有類型轉發設置為行動類型的新位置。

| 來源程式集 | 目標程式集 | 類型                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *系統.安全.許可權.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *系統.安全.許可權.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *系統.Windows.擴展.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> 為了盡量減少移植摩擦,在類型中保留了存儲和檢索與以下屬性相關的資訊的功能`XamlAccessLevel`。
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>後續步驟

- [瞭解如何將 .NET 框架 WPF 應用移植到 .NET 核心。](convert-project-from-net-framework.md)
