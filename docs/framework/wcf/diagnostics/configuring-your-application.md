---
title: 設定您的應用程式
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 1844c20ef961f191fb667e31d548518b193a7134
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803646"
---
# <a name="configuring-your-application"></a>設定您的應用程式
Windows Communication Foundation (WCF) 會使用.NET 組態系統，並可讓您設定服務在電腦和應用程式的範圍。  
  
 WCF 所定義的組態設定位於`<system.serviceModel>`區段群組。 如需如何設定 WCF 服務的詳細資訊，請參閱下列主題：  
  
-   [設定服務](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 應用程式定義的組態設定會定義在 `<appSettings>` 節群組中。 如需.NET 組態檔中的應用程式設定的詳細資訊，請參閱[ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)。  
  
## <a name="using-the-configuration-editor"></a>使用組態編輯器  
 WCF[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)可讓管理員和開發人員建立及修改 WCF 服務使用圖形化使用者介面的組態設定。 使用這個工具，您可以管理設定 WCF 繫結、 行為、 服務和診斷，而不用直接編輯 XML 組態檔。  
  
## <a name="editing-configuration-files-in-visual-studio"></a>在 Visual Studio 中編輯組態檔  
 若要編輯的 Visual Studio 中的 WCF 服務專案的組態檔，以滑鼠右鍵按一下 [**方案總管] 中**選擇**編輯 WCF 組態**操作功能表項目。 這會啟動[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。  
  
> [!NOTE]
>  如果您編輯 Visual Studio 中的 WCF Web 服務專案的組態檔，以滑鼠右鍵按一下它在**方案總管 中**，請注意，**編輯 WCF 組態**操作功能表項目已遺失。 若要解決這個問題，請按一下**工具**功能表上，選擇  **WCF 服務組態編輯器**。 在這之後，您可以以滑鼠右鍵按一下組態檔，並使用**編輯 WCF 組態**操作功能表項目。  
  
## <a name="see-also"></a>另請參閱  
 [設定編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [設定服務](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
