---
title: "如何：設定應用程式以支援 .NET Framework 4 或 4.5 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring apps to support .NET Framework 4
- .NET Framework 4, configuring apps
- .NET Framework 4.5, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
caps.latest.revision: 14
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 86dce70e92c0e424b169b6fc58e87c5652ebcb69
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-45"></a>如何：設定應用程式以支援 .NET Framework 4 或 4.5
所有裝載通用語言執行平台 (CLR) 的應用程式都必須啟動或「啟用」CLR，才能執行 Managed 程式碼。 通常，.NET Framework 應用程式會在本身建置所在的 CLR 版本上執行，但是您可以使用應用程式組態檔 (有時稱為 app.config 檔案) 變更桌面應用程式的這個行為。 不過，您無法使用應用程式組態檔變更 Windows 市集應用程式或 Windows Phone 應用程式的預設啟用行為。 本文將說明如何讓您的桌面應用程式在另一個 .NET Framework 版本上執行，並且提供如何鎖定 4 或 4.5 版做為目標。  
  
 執行應用程式所在的 .NET Framework 版本是依照下列順序決定：  
  
-   組態檔。  
  
     如果應用程式組態檔包含指定一個或多個 .NET Framework 版本的 [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 項目，而且使用者的電腦上有其中一個版本，則應用程式會在該版本上執行。 組態檔會依 [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 項目列出的順序讀取這些項目，並且使用使用者電腦上所列的第一個 .NET Framework 版本。 (針對 1.0 版使用 [\<requiredRuntime> 元素](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md))。  
  
-   編譯的版本。  
  
     如果沒有組態檔，但是使用者的電腦上有建置應用程式所在的 .NET Framework 版本，則應用程式會在該版本上執行。  
  
-   安裝的最新版本。  
  
     如果沒有建置應用程式所在的 .NET Framework 版本，而且組態檔並未在 [\<supportedRuntime> 元素](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)中指定版本，則應用程式會嘗試以使用者電腦中存在的最新 .NET Framework 版本執行。  
  
     不過，.NET Framework 1.0、1.1、2.0、3.0 和 3.5 應用程式不會自動在 .NET Framework 4 (含) 以後版本上執行，而且在某些情況下，使用者可能會收到錯誤以及安裝 .NET Framework 3.5 的提示。 因為不同版本的 Windows 系統包含不同版本的 .NET Framework，因此啟用行為也會取決於使用者的作業系統。 如果您的應用程式同時支援 .NET Framework 3.5 和 4 (含) 以後版本，建議您在組態檔中使用多個項目指出這種情況，避免發生 .NET Framework 初始化錯誤。 如需詳細資訊，請參閱[版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)。  
  
 即使電腦中安裝的是 .NET Framework 3.5，您也可以設定讓自己的 .NET Framework 3.5 應用程式在 .NET Frramework 4 或 4.5 上執行，以充分運用 .NET Framework 4 和 4.5 版的效能增強優勢。  
  
> [!IMPORTANT]
>  建議您一律在支援的每一個 .NET Framework 版本上測試您的應用程式。 如需將應用程式升級為支援最新 .NET Framework 版本的詳細資訊，請參閱[版本相容性](../../../docs/framework/migration-guide/version-compatibility.md)。  
  
 如需修改 .NET Framework 1.0 和 1.1 應用程式以支援 Windows 7 及 Windows 8 的詳細資訊，請參閱[從 .NET Framework 1.1 移轉](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)。  
  
### <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-45"></a>若要設定讓您的應用程式在 .NET Framework 4 或 4.5 上執行  
  
1.  加入或尋找 .NET Framework 專案的組態檔。 應用程式的組態檔與應用程式位於相同的目錄中且名稱相同，不過其副檔名為 .config。 例如，如果應用程式名為 MyExecutable.exe，則應用程式組態檔會命名為 MyExecutable.exe.config。  
  
     若要加入組態檔，請在 Visual Studio 功能表列上選擇 [專案]、[加入新項目]。 從左窗格選擇 [一般]，然後選擇 [組態檔]。  將組態檔命名為*應用程式名稱*.exe.config。 這些功能表選項不適用於 Windows 市集應用程式或 Windows Phone 應用程式專案，因為您無法變更這些平台的啟用原則。  
  
2.  將 [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 元素加入至應用程式組態檔，如下所示：  
  
    ```  
    <configuration>  
      <startup>  
        <supportedRuntime version="<version>"/>  
      </startup>  
    </configuration>  
  
    ```  
  
     其中 *\<version>* 會指定與應用程式支援的 .NET Framework 版本對應的 CLR 版本。 使用下列字串：  
  
    -   .NET Framework 1.0："v1.0.3705"  
  
    -   .NET Framework 1.1："v1.1.4322"  
  
    -   .NET Framework 2.0、3.0 和 3.5："v2.0.50727"  
  
    -   .NET Framework 4 和 4.5 (包括像是 4.5.1 這類點發行版本)："v4.0"  
  
     您可以加入多個 [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 元素並且依偏好列出，以便指定支援多種版本的 .NET Framework。  
  
 下表將示範電腦上安裝的應用程式組態檔設定和 .NET Framework 版本如何決定用來執行 .NET Framework 3.5 應用程式的版本。 這些範例為 .NET Framework 3.5 應用程式專屬，不過您可以使用類似的邏輯鎖定使用舊版 .NET Framework 建置的應用程式。 請注意，.NET Framework 2.0 版本號碼 (v2.0.50727) 是在應用程式組態檔中用來指定 .NET Framework 3.5。  
  
|App.config 檔案設定|在安裝 3.5 版的電腦上|在安裝 3.5 版和 4 或 4.5 版的電腦上|在安裝 4 或 4.5 版的電腦上|  
|-|-|-|-|  
|無|在 3.5 上執行|在 3.5 上執行|顯示錯誤訊息，提示使用者安裝正確的版本*|  
|`<supportedRuntime version="v2.0.50727"/>`|在 3.5 上執行|在 3.5 上執行|顯示錯誤訊息，提示使用者安裝正確的版本*|  
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|在 3.5 上執行|在 3.5 上執行|在 4 或 4.5 上執行|  
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|在 3.5 上執行|在 4 或 4.5 上執行|在 4 或 4.5 上執行|  
|`<supportedRuntime version="v4.0"/>`|顯示錯誤訊息，提示使用者安裝正確的版本*|在 4 或 4.5 上執行|在 4 或 4.5 上執行|  
  
 \*如需有關這個錯誤訊息及避免出現這個錯誤訊息的詳細資訊，請參閱 [.NET Framework 初始化錯誤：管理使用者經驗](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)。  
  
## <a name="see-also"></a>另請參閱  
 [從 .NET Framework 1.1 移轉](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [移轉手冊](../../../docs/framework/migration-guide/index.md)
