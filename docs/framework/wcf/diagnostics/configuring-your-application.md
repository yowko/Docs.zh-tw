---
title: "設定您的應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 064f396d0a757e5b2f5f12c4a2a836b74f5e66a6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-your-application"></a>設定您的應用程式
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會使用 .NET 組態系統，並讓您在機器和應用程式範圍內設定服務。  
  
 由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 定義的組態設定位於 `<system.serviceModel>` 節群組中。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的詳細資訊，請參閱下列主題：  
  
-   [設定服務](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 應用程式定義的組態設定會定義在 `<appSettings>` 節群組中。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]應用程式設定.NET 設定檔中，請參閱[ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)。  
  
## <a name="using-the-configuration-editor"></a>使用組態編輯器  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)可讓系統管理員和開發人員建立及修改組態設定[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務以使用圖形化使用者介面。 有了這項工具，您可以管理 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結、行為、服務及診斷的設定，而不用直接編輯 XML 組態檔。  
  
## <a name="editing-configuration-files-in-visual-studio"></a>在 Visual Studio 中編輯組態檔  
 若要編輯的組態檔[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務專案中的[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]，以滑鼠右鍵按一下 [**方案總管] 中**選擇**編輯 WCF 組態**操作功能表項目。 這會啟動[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。  
  
> [!NOTE]
>  如果您編輯的組態檔[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]中的 Web 服務專案[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]以滑鼠右鍵按一下它在**方案總管 中**，請注意，**編輯 WCF 組態**操作功能表項目遺漏. 若要解決這個問題，請按一下**工具**功能表上，選擇  **WCF 服務組態編輯器**。 在這之後，您可以以滑鼠右鍵按一下組態檔，並使用**編輯 WCF 組態**操作功能表項目。  
  
## <a name="see-also"></a>另請參閱  
 [設定編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [設定服務](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
