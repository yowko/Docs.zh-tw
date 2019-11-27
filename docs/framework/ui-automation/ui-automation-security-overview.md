---
title: UI 自動化安全性概觀
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 70d24c3dcc531abcec6d4dce75b5f0b31757e0c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448779"
---
# <a name="ui-automation-security-overview"></a>UI 自動化安全性概觀

> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。

本總覽描述 Windows Vista 中 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 的安全性模型。

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>使用者帳戶控制

安全性是 Windows Vista 的主要焦點，而創新功能是讓使用者以標準（非系統管理員）的使用者身分執行，而不需要遭到封鎖，而無法執行需要較高許可權的應用程式和服務。

在 Windows Vista 中，大部分的應用程式都是以標準或系統管理權杖來提供。 如果無法將應用程式識別為系統管理應用程式，根據預設，它就會啟動為標準應用程式。 在可啟動識別為系統管理的應用程式之前，Windows Vista 會提示使用者同意以提高許可權執行應用程式。 即使使用者是本機 Administrators 群組的成員，預設也會顯示同意提示，因為在需要管理認證的應用程式或系統元件要求執行權限之前，系統管理員會以標準使用者身分執行。

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>需要更高權限的工作

當使用者嘗試執行需要系統管理許可權的工作時，Windows Vista 會顯示對話方塊，詢問使用者是否同意繼續進行。 這個對話方塊會防止跨處理序通訊的存取，因此惡意軟體無法模擬使用者輸入。 同樣地，其他處理序通常也無法存取桌面登入畫面。

UI 自動化用戶端必須與其他處理序通訊，其中部分可能會以更高的權限層級執行。 用戶端也可能需要存取一般不會對其他處理序顯示的系統對話方塊。 因此， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 用戶端必須受系統信任，而且必須以特殊權限執行。

若要受信任以便與以較高權限層級執行的應用程式通訊，必須簽署應用程式。

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>資訊清單檔

若要取得受保護系統 UI 的存取權，應用程式必須以包含 `requestedExecutionLevel` 標記中 `uiAccess` 屬性的資訊清單檔建立，如下所示：

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

`uiAccess` 預設為 "false";也就是說，如果省略屬性，或元件沒有資訊清單，應用程式將無法取得受保護 UI 的存取權。
