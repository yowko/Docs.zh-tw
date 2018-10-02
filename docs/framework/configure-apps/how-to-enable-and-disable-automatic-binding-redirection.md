---
title: 如何：啟用和停用自動繫結重新導向
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9b9c9cbdb89ccf67942dcccee37ea410c6fa39a5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036191"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>如何：啟用和停用自動繫結重新導向

在 Visual Studio 中為目標的應用程式的編譯時[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]和更新版本中，繫結重新導向可能會自動加入至應用程式組態檔覆寫組件統一。 如果您的應用程式或其元件參考相同組件的多個版本，即使您在應用程式的組態檔中手動指定繫結重新導向，仍會加入繫結重新導向。 自動繫結重新導向功能會影響傳統桌面應用程式和 web 應用程式為目標[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]或更新版本中，雖然行為會稍有不同的 web 應用程式。 如果您現有的應用程式是以舊版的 .NET Framework 為目標，就可以啟用自動繫結重新導向，如果您要保留手動撰寫的繫結重新導向，可以停用這項功能。

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>停用自動繫結重新導向桌面應用程式中

在以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 和較新版本為目標的傳統桌面應用程式中，自動繫結重新導向預設為啟用。 繫結重新導向會在應用程式進行編譯時加入至輸出組態檔 (app.config)，並且覆寫可能進行的組件統一。 來源 app.config 檔案則不會加以修改。 您可以修改應用程式的專案檔停用這項功能。

1. 開啟專案檔案進行編輯使用下列方法之一：

   - 在 Visual Studio 中，選取專案**方案總管 中**，然後選擇**在檔案總管 中開啟資料夾**從捷徑功能表。 在 [檔案總管] 中，尋找專案 （.csproj 或.vbproj） 檔，並在記事本中開啟它。
   - 在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下專案，然後選擇**卸載專案**。 同樣地，以滑鼠右鍵按一下已卸載的專案，然後選擇 [**編輯 [projectname.csproj]]**。

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
   - 在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下專案，然後選擇**卸載專案**。 同樣地，以滑鼠右鍵按一下已卸載的專案，然後選擇 [**編輯 [projectname.csproj]]**。

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

在 Web 應用程式中，自動繫結重新導向是以不同的方式實作。 由於 Web 應用程式的來源組態檔 (web.config) 必須經過修改，因此繫結重新導向不會自動加入至組態檔。 不過，如果發生繫結衝突，Visual Studio 會通知您，那麼您就可以加入繫結重新導向來解決衝突。 由於系統一律提示您新增繫結重新導向，您不需要明確停用此功能的 web 應用程式。

若要新增繫結重新導向到 web.config 檔案：

1. 在 Visual Studio 中編譯應用程式，並檢查是否有建置警告。

   ![建置組件參考衝突的警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. 如果有組件繫結衝突，則會出現警告。 按兩下該警告，或選取警告並按下**Enter**。

   對話方塊隨即出現，可讓您將必要的繫結重新導向自動加入至來源 web.config 檔。

   ![繫結重新導向的權限 對話方塊](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>另請參閱

- [\<bindingRedirect > 項目](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
