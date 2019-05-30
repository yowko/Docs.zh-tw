---
title: 啟用或停用自動產生繫結重新導向
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b6c9c3508c53e8a68a3f7e1cb12b6b6c95600e7b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380095"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>HOW TO：啟用和停用自動繫結重新導向

當您編譯.NET Framework 4.5.1 為目標的 Visual Studio 和更新版本中的應用程式時，繫結重新導向可能會自動加入至應用程式組態檔覆寫組件統一。 如果您的應用程式或其元件參考相同組件的多個版本，即使您在應用程式的組態檔中手動指定繫結重新導向，仍會加入繫結重新導向。 自動繫結重新導向功能會影響傳統型應用程式和 web 應用程式目標為.NET Framework 4.5.1 或更新版本，但行為會稍有不同的 web 應用程式。 如果您有現有的應用程式先前版本為目標的.NET Framework 中，或如果您想要以手動方式撰寫繫結重新導向，您可以停用這項功能，您可以啟用自動繫結重新導向。

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>停用自動繫結重新導向桌面應用程式中

在.NET Framework 4.5.1 及更新版本為目標的 Windows 傳統型應用程式的預設會啟用自動繫結重新導向。 繫結重新導向新增至輸出組態 (**app.config**) 檔案在編譯應用程式時，並覆寫可能進行的組件統一。 來源**app.config**則不會修改檔案。 藉由修改應用程式的專案檔，或取消選取核取方塊，在 Visual Studio 中的專案屬性中，您可以停用這項功能。

### <a name="disable-through-project-properties"></a>停用透過專案屬性

如果您有 Visual Studio 2017 15.7 版或更新版本時，您可以輕鬆停用專案屬性頁中的自動產生繫結重新導向。

1. 以滑鼠右鍵按一下 [方案總管]  中的專案，然後選取 [屬性]  。

2. 在 **應用程式**頁面上，取消核取**自動產生繫結重新導向**選項。

3. 按下**Ctrl**+**S**儲存的變更。

### <a name="disable-manually-in-the-project-file"></a>停用手動方式在專案檔

1. 開啟專案檔案進行編輯使用下列方法之一：

   - 在 Visual Studio 中，選取專案**方案總管 中**，然後選擇**在檔案總管 中開啟資料夾**從捷徑功能表。 在 [檔案總管] 中，尋找專案 （.csproj 或.vbproj） 檔，並在記事本中開啟它。
   - 在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下專案，然後選擇**卸載專案**。 同樣地，以滑鼠右鍵按一下已卸載的專案，然後選擇 [**編輯 [projectname.csproj]]** 。

2. 在專案檔中尋找下列屬性項目：

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. 將 `true` 變更為 `false`：

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>以手動方式啟用自動繫結重新導向

您可以啟用自動繫結重新導向，現有的應用程式中較舊版本為目標的.NET Framework 中，或在情況下，您不會自動加入重新導向系統提示時。 如果您較新的 framework 版本為目標，但不要收到自動提示加入重新導向，您可能會建議您重新對應組件的組建輸出。

1. 開啟專案檔案進行編輯使用下列方法之一：

   - 在 Visual Studio 中，選取專案**方案總管 中**，然後選擇**在檔案總管 中開啟資料夾**從捷徑功能表。 在 [檔案總管] 中，尋找專案 （.csproj 或.vbproj） 檔，並在記事本中開啟它。
   - 在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下專案，然後選擇**卸載專案**。 同樣地，以滑鼠右鍵按一下已卸載的專案，然後選擇 [**編輯 [projectname.csproj]]** 。

2. 將下列項目新增至第一個組態屬性群組 (在\<PropertyGroup > 標記):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   下列範例顯示的範例專案檔案與插入的項目：

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. 編譯您的應用程式。

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>啟用 web 應用程式中的自動繫結重新導向

在 Web 應用程式中，自動繫結重新導向是以不同的方式實作。 因為來源設定 (**web.config**) 檔必須經過修改的 web 應用程式中，繫結重新導向不會自動新增至組態檔。 不過，如果發生繫結衝突，Visual Studio 會通知您，那麼您就可以加入繫結重新導向來解決衝突。 由於系統一律提示您新增繫結重新導向，您不需要明確停用此功能的 web 應用程式。

若要新增繫結重新導向**web.config**檔案：

1. 在 Visual Studio 中編譯應用程式，並檢查是否有建置警告。

   ![建置組件參考衝突的警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. 如果有組件繫結衝突，則會出現警告。 按兩下該警告，或選取警告並按下**Enter**。

   對話方塊，可讓您自動新增必要的繫結重新導向至來源**web.config**檔案隨即出現。

   ![繫結重新導向的權限 對話方塊](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>另請參閱

- [\<bindingRedirect > 項目](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
