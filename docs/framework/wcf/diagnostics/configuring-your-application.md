---
title: 設定您的應用程式
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 04ddce4755ce30b7d46c3bd54024af08361d96ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536077"
---
# <a name="configuring-your-application"></a>設定您的應用程式
Windows Communication Foundation (WCF) 使用 .NET 設定系統，並可讓您在電腦和應用程式範圍設定服務。  
  
 WCF 定義的設定設定位於 `<system.serviceModel>` 區段群組中。 如需有關如何設定 WCF 服務的詳細資訊，請參閱下列主題：  
  
- [設定服務](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 應用程式定義的組態設定會定義在 `<appSettings>` 節群組中。 如需 .NET 設定檔中應用程式設定的詳細資訊，請參閱 [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)) 。  
  
## <a name="using-the-configuration-editor"></a>使用組態編輯器  
 WCF 設定 [編輯器工具 ( # A0) ](../configuration-editor-tool-svcconfigeditor-exe.md) 可讓系統管理員和開發人員使用圖形化使用者介面來建立和修改 WCF 服務的設定。 使用此工具，您可以管理 WCF 系結、行為、服務及診斷的設定，而不需要直接編輯 XML 設定檔。  
  
## <a name="editing-configuration-files-in-visual-studio"></a>在 Visual Studio 中編輯組態檔  
 若要在 Visual Studio 中編輯 WCF 服務專案的設定檔，請在 **方案總管** 中以滑鼠右鍵按一下該專案，然後選擇 [ **編輯 WCF** 設定] 內容功能表項目。 這會啟動設定 [編輯器工具 ( # A0) ](../configuration-editor-tool-svcconfigeditor-exe.md)。  
  
> [!NOTE]
> 如果您 Visual Studio 在 **方案總管**中以滑鼠右鍵按一下 WCF Web 服務專案的設定檔來編輯該專案的設定檔，請注意，[ **編輯 wcf** 設定] 內容功能表項目已遺失。 若要解決這個問題，請按一下 [ **工具** ] 功能表，然後選擇 [ **WCF 服務設定編輯器**]。 之後，您可以在設定檔上按一下滑鼠右鍵，然後使用 [ **編輯 WCF** 設定] 內容功能表項目。  
  
## <a name="see-also"></a>另請參閱

- [組態編輯器工具 (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [設定服務](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
