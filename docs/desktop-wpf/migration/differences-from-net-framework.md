---
title: .NET Framework 和 .NET Core 之間的差異
description: 說明 Windows Presentation Foundation （WPF）和 .NET Core WPF 的 .NET Framework 執行之間的差異。 在遷移您的應用程式時，您應該考慮這些不相容性。
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

本文說明 .NET Core 上的 Windows Presentation Foundation （WPF）與 .NET Framework 之間的差異。 適用于 .NET Core 的 WPF 是一個開放原始碼[架構](https://github.com/dotnet/wpf)，會從 .NET Framework 原始程式碼的原始 WPF 派生。

.NET Core 不支援 .NET Framework 的幾項功能。 如需不支援技術的詳細資訊，請參閱[.Net Core 上無法使用的 .NET Framework 技術](../../core/porting/net-framework-tech-unavailable.md)。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>SDK 樣式專案

.NET Core 使用 SDK 樣式的專案檔。 這些專案檔不同于 Visual Studio 所管理的傳統 .NET Framework 專案檔案。 若要將您的 .NET Framework WPF 應用程式遷移至 .NET Core，您必須轉換專案。 如需詳細資訊，請參閱[將 WPF 應用程式遷移至 .Net Core 3.0](convert-project-from-net-framework.md)。

## <a name="nuget-package-references"></a>NuGet 封裝參考

如果您的 .NET Framework 應用程式在*封裝 .config*檔案中列出其 NuGet 相依性，請[`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)遷移至下列格式：

1. 在 Visual Studio 中，開啟 [**方案總管**] 窗格。
1. 在 WPF 專案中，以滑鼠右鍵按一下 [**封裝** > ]，**將 [config.xml] 遷移至 PackageReference**。

![升級至 PackageReference](media/differences-from-net-framework/package-reference-migration.png)

隨即會出現一個對話方塊，顯示計算的最上層 NuGet 相依性，並詢問哪些其他 NuGet 套件應該升級為最上層。 選取 **[確定]** ，將會從專案中移除*封裝 .config*檔案， `<PackageReference>`而元素會加入至專案檔。

當您的專案`<PackageReference>`使用時，封裝不會儲存在本機的*封裝*資料夾中，而是以全域方式儲存。 開啟專案檔，並移除任何`<Analyzer>`參考 [*封裝*] 資料夾的元素。 這些分析器會自動包含在 NuGet 套件參考中。

## <a name="code-access-security"></a>程式碼存取安全性

.Net Core 或適用于 .NET Core 的 WPF 不支援代碼啟用安全性（CAS）。 所有與 CAS 相關的功能都會被視為完全信任的假設。 適用于 .NET Core 的 WPF 會移除 CAS 相關程式碼。 這些類型的公用 API 介面仍然存在，以確保這些類型的呼叫會成功。

公開定義的 CAS 相關類型已移出 WPF 元件和核心 .NET 程式庫元件。 WPF 元件會將類型轉送設定為已移動類型的新位置。

| 來源元件 | 目標群組件 | 類型                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *系統安全性許可權 .dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *系統安全性許可權 .dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *System.web 副檔名 .dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> 為了儘量減少移植的摩擦，儲存和抓取下列屬性相關資訊的功能已保留在`XamlAccessLevel`類型中。
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>後續步驟

- [瞭解如何將 .NET Framework WPF 應用程式移植到 .NET Core。](convert-project-from-net-framework.md)
