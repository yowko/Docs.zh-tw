---
title: "如何：啟用和停用自動繫結重新導向"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 83b004934c303c95bdc4e6edb6031a86e2b1a6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>如何：啟用和停用自動繫結重新導向
從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，當您編譯目標為 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 的應用程式時，繫結重新導向會自動加入至應用程式組態檔以覆寫組件統一。 如果您的應用程式或其元件參考相同組件的多個版本，即使您在應用程式的組態檔中手動指定繫結重新導向，仍會加入繫結重新導向。 自動繫結重新導向功能會影響以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 為目標的傳統桌面應用程式和 Web 應用程式，不過 Web 應用程式的行為稍有不同。 如果您現有的應用程式是以舊版的 .NET Framework 為目標，就可以啟用自動繫結重新導向，如果您要保留手動撰寫的繫結重新導向，可以停用這項功能。  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a>在桌面應用程式中停用自動繫結重新導向  
 在以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 和較新版本為目標的傳統桌面應用程式中，自動繫結重新導向預設為啟用。 繫結重新導向會在應用程式進行編譯時加入至輸出組態檔 (app.config)，並且覆寫可能進行的組件統一。 來源 app.config 檔案則不會加以修改。 您可以修改應用程式的專案檔停用這項功能。  
  
#### <a name="to-disable-automatic-binding-redirects"></a>若要停用自動繫結重新導向  
  
1.  在 Visual Studio 中選取專案**方案總管 中**，然後選擇 **在檔案總管 中開啟資料夾**從捷徑功能表。  
  
2.  在 [檔案總管] 中尋找專案檔 (.csproj 或 .vbproj)，然後在 [記事本] 中開啟它。  
  
3.  在專案檔中尋找下列屬性項目：  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  將 `true` 變更為 `false`：  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a>手動啟用自動繫結重新導向  
 在以舊版 .NET Framework 為目標的現有應用程式中，或是當系統未自動提示您加入重新導向時，您可以啟用自動繫結重新導向。 如果您是以較新版架構為目標，但系統未自動提示您加入重新導向，您可能會取得建議您重新對應組件的組建輸出。  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a>手動加入自動繫結重新導向屬性  
  
1.  在 Visual Studio 中選取專案**方案總管 中**，然後選擇 **在檔案總管 中開啟資料夾**從捷徑功能表。  
  
2.  在 [檔案總管] 中尋找專案檔 (.csproj 或 .vbproj)，然後在 [記事本] 中開啟它。  
  
3.  將下列項目加入至第一個組態屬性群組 (下\<PropertyGroup > 標記):  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     下面顯示已插入項目的專案檔範例。  
  
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
  
4.  編譯您的應用程式。  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a>在 Web 應用程式中啟用自動繫結重新導向  
 在 Web 應用程式中，自動繫結重新導向是以不同的方式實作。 由於 Web 應用程式的來源組態檔 (web.config) 必須經過修改，因此繫結重新導向不會自動加入至組態檔。 不過，如果發生繫結衝突，Visual Studio 會通知您，那麼您就可以加入繫結重新導向來解決衝突。 由於系統一律提示您加入繫結重新導向，因此您不需要明確停用 Web 應用程式的這項功能。  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a>若要將繫結重新導向加入至 web.config 檔  
  
1.  在 Visual Studio 中編譯應用程式，並檢查是否有建置警告。  
  
     ![建置組件參考衝突的警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")  
  
2.  如果有組件繫結衝突，則會出現警告。 按兩下警告  (鍵盤： 選取警告並按下**Enter**。)  
  
     對話方塊隨即出現，可讓您將必要的繫結重新導向自動加入至來源 web.config 檔。  
  
     ![繫結重新導向 權限對話方塊](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")  
  
## <a name="see-also"></a>另請參閱  
 [\<bindingRedirect > 項目](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
