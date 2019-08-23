---
title: 啟用或停用自動產生的系結重新導向
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: 178d5070dd7018bbc0fce474cdd0b31ba3d17f77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913038"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>作法：啟用和停用自動繫結重新導向

當您在以 .NET Framework 4.5.1 和更新版本為目標的 Visual Studio 中編譯應用程式時, 可能會自動將系結重新導向新增至應用程式佈建檔, 以覆寫元件統一。 如果您的應用程式或其元件參考相同組件的多個版本，即使您在應用程式的組態檔中手動指定繫結重新導向，仍會加入繫結重新導向。 自動系結重新導向功能會影響以 .NET Framework 4.5.1 或更新版本為目標的桌面應用程式和 web 應用程式, 雖然 web 應用程式的行為稍有不同。 如果您現有的應用程式是以舊版 .NET Framework 為目標, 您可以啟用自動系結重新導向, 如果您想要手動編寫系結重新導向, 可以停用這項功能。

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>在桌面應用程式中停用自動系結重新導向

針對以 .NET Framework 4.5.1 和更新版本為目標的 Windows 桌面應用程式, 預設會啟用自動系結重新導向。 編譯應用程式時, 會將系結重新導向新增至輸出設定 (**app.config**) 檔案, 並覆寫可能會發生的元件統一。 未修改來源**app.config**檔案。 您可以藉由修改應用程式的專案檔, 或在 Visual Studio 的專案屬性中取消勾選核取方塊, 來停用這項功能。

### <a name="disable-through-project-properties"></a>透過專案屬性停用

如果您有 Visual Studio 2017 15.7 版或更新版本, 您可以輕鬆地在專案的屬性頁中停用自動產生的系結重新導向。

1. 以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [屬性]。

2. 在 [**應用程式**] 頁面上, 取消核取 [**自動產生**系結重新導向] 選項。

3. 按**Ctrl** + **S**以儲存變更。

### <a name="disable-manually-in-the-project-file"></a>在專案檔中手動停用

1. 使用下列其中一種方法開啟專案檔進行編輯:

   - 在 Visual Studio 中, 選取**方案總管**中的專案, 然後從快捷方式功能表選擇 [**在檔案瀏覽器中開啟資料夾**]。 在 [檔案管理器] 中, 尋找專案 (.csproj 或. vbproj) 檔案, 然後在 [記事本] 中開啟。
   - 在 Visual Studio 的**方案總管**中, 以滑鼠右鍵按一下專案, 然後選擇 **[卸載專案**]。 再次以滑鼠右鍵按一下卸載的專案, 然後選擇 **[編輯 [專案名稱 .csproj]]** 。

2. 在專案檔中尋找下列屬性項目：

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. 將 `true` 變更為 `false`：

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>手動啟用自動系結重新導向

您可以在以舊版 .NET Framework 為目標的現有應用程式中啟用自動系結重新導向, 或在不會自動提示您加入重新導向的情況下進行。 如果您的目標是較新版本的 framework, 但未自動提示您加入重新導向, 您可能會取得建議您重新對應元件的組建輸出。

1. 使用下列其中一種方法開啟專案檔進行編輯:

   - 在 Visual Studio 中, 選取**方案總管**中的專案, 然後從快捷方式功能表選擇 [**在檔案瀏覽器中開啟資料夾**]。 在 [檔案管理器] 中, 尋找專案 (.csproj 或. vbproj) 檔案, 然後在 [記事本] 中開啟。
   - 在 Visual Studio 的**方案總管**中, 以滑鼠右鍵按一下專案, 然後選擇 **[卸載專案**]。 再次以滑鼠右鍵按一下卸載的專案, 然後選擇 **[編輯 [專案名稱 .csproj]]** 。

2. 將下列元素新增至第一個設定屬性群組 (在\<PropertyGroup > 標記底下):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   以下顯示已插入元素的範例專案檔:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. 編譯您的應用程式。

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>在 web 應用程式中啟用自動系結重新導向

在 Web 應用程式中，自動繫結重新導向是以不同的方式實作。 因為必須修改 web 應用程式的來源設定 (**web.config**) 檔案, 所以不會自動將系結重新導向新增至設定檔。 不過，如果發生繫結衝突，Visual Studio 會通知您，那麼您就可以加入繫結重新導向來解決衝突。 由於系統一律會提示您加入系結重新導向, 因此您不需要明確停用 web 應用程式的這項功能。

若要將系結重新導向加入至**web.config**檔案:

1. 在 Visual Studio 中編譯應用程式，並檢查是否有建置警告。

   ![元件參考衝突的組建警告](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. 如果有組件繫結衝突，則會出現警告。 按兩下警告, 或選取警告, 然後按**enter**鍵。

   可讓您自動將必要的系結重新導向加入至來源**web.config**檔案的對話方塊隨即出現。

   [系結重新![導向許可權] 對話方塊](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>另請參閱

- [\<bindingRedirect > 元素](./file-schema/runtime/bindingredirect-element.md)
- [重新導向組件版本](redirect-assembly-versions.md)
