---
title: UI 自動化安全性概觀
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 8b798aef528cccdedb1fcaa53c1782632037600d
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133791"
---
# <a name="ui-automation-security-overview"></a>UI 自動化安全性概觀

> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。

本概觀說明 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 中 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]的安全性模型。

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>使用者帳戶控制

安全性是 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] 的主要焦點，在所有創新功能中，這項功能可以讓使用者以標準 (非系統管理員) 使用者身分執行，但不會被封鎖而無法執行需要更高權限的應用程式和服務。

在 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]中，大部分的應用程式都具備標準或系統管理語彙基元。 如果無法將應用程式識別為系統管理應用程式，根據預設，它就會啟動為標準應用程式。 識別為系統管理的應用程式啟動之前， [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] 會提示使用者是否同意以提高權限的方式執行應用程式。 即使使用者是本機 Administrators 群組的成員，預設也會顯示同意提示，因為在需要管理認證的應用程式或系統元件要求執行權限之前，系統管理員會以標準使用者身分執行。

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>需要更高權限的工作

當使用者嘗試執行需要系統管理權限的工作時， [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] 會顯示對話方塊，詢問使用者是否同意繼續進行。 這個對話方塊會防止跨處理序通訊的存取，因此惡意軟體無法模擬使用者輸入。 同樣地，其他處理序通常也無法存取桌面登入畫面。

使用者介面自動化用戶端必須與其他處理序通訊，其中部分可能會以更高的權限層級執行。 用戶端也可能需要存取一般不會對其他處理序顯示的系統對話方塊。 因此， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 用戶端必須受系統信任，而且必須以特殊權限執行。

若要受信任以便與以較高權限層級執行的應用程式通訊，必須簽署應用程式。

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>資訊清單檔

若要取得受保護系統 UI 的存取權, 應用程式必須使用包含`uiAccess` `requestedExecutionLevel`標記中屬性的資訊清單檔來建立, 如下所示:

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

這個程式碼中 `level` 屬性的值只是範例。

`uiAccess`預設為 "false";也就是說, 如果省略屬性, 或元件沒有資訊清單, 應用程式將無法取得受保護 UI 的存取權。
