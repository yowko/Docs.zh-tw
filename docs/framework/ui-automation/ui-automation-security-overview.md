---
title: UI 自動化安全性概觀
description: 閱讀 Microsoft UI 自動化的安全性模式總覽。 瞭解使用者帳戶控制、需要更高許可權的工作，以及資訊清單檔案。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: d483f282db8ce8e5653d6d83361fa44df05f63f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163146"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="07e18-104">UI 自動化安全性概觀</span><span class="sxs-lookup"><span data-stu-id="07e18-104">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="07e18-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="07e18-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="07e18-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="07e18-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="07e18-107">本總覽描述 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Windows Vista 中的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="07e18-107">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="07e18-108">使用者帳戶控制</span><span class="sxs-lookup"><span data-stu-id="07e18-108">User Account Control</span></span>

<span data-ttu-id="07e18-109">安全性是 Windows Vista 的主要焦點，而創新功能是讓使用者以標準（非系統管理員）的使用者身分執行，而不需要遭到封鎖，而無法執行需要較高許可權的應用程式和服務。</span><span class="sxs-lookup"><span data-stu-id="07e18-109">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="07e18-110">在 Windows Vista 中，大部分的應用程式都是以標準或系統管理權杖來提供。</span><span class="sxs-lookup"><span data-stu-id="07e18-110">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="07e18-111">如果無法將應用程式識別為系統管理應用程式，根據預設，它就會啟動為標準應用程式。</span><span class="sxs-lookup"><span data-stu-id="07e18-111">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="07e18-112">在可啟動識別為系統管理的應用程式之前，Windows Vista 會提示使用者同意以提高許可權執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="07e18-112">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="07e18-113">即使使用者是本機 Administrators 群組的成員，預設也會顯示同意提示，因為在需要管理認證的應用程式或系統元件要求執行權限之前，系統管理員會以標準使用者身分執行。</span><span class="sxs-lookup"><span data-stu-id="07e18-113">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="07e18-114">需要更高權限的工作</span><span class="sxs-lookup"><span data-stu-id="07e18-114">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="07e18-115">當使用者嘗試執行需要系統管理許可權的工作時，Windows Vista 會顯示對話方塊，詢問使用者是否同意繼續進行。</span><span class="sxs-lookup"><span data-stu-id="07e18-115">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="07e18-116">這個對話方塊會防止跨處理序通訊的存取，因此惡意軟體無法模擬使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="07e18-116">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="07e18-117">同樣地，其他處理序通常也無法存取桌面登入畫面。</span><span class="sxs-lookup"><span data-stu-id="07e18-117">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="07e18-118">使用者介面自動化用戶端必須與其他處理序通訊，其中部分可能會以更高的權限層級執行。</span><span class="sxs-lookup"><span data-stu-id="07e18-118">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="07e18-119">用戶端也可能需要存取一般不會對其他處理序顯示的系統對話方塊。</span><span class="sxs-lookup"><span data-stu-id="07e18-119">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="07e18-120">因此， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 用戶端必須受系統信任，而且必須以特殊權限執行。</span><span class="sxs-lookup"><span data-stu-id="07e18-120">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="07e18-121">若要受信任以便與以較高權限層級執行的應用程式通訊，必須簽署應用程式。</span><span class="sxs-lookup"><span data-stu-id="07e18-121">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="07e18-122">資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="07e18-122">Manifest Files</span></span>

<span data-ttu-id="07e18-123">若要取得受保護系統 UI 的存取權，應用程式必須使用包含標記中屬性的資訊清單檔來建立，如下所示 `uiAccess` `requestedExecutionLevel` ：</span><span class="sxs-lookup"><span data-stu-id="07e18-123">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

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

<span data-ttu-id="07e18-124">這個程式碼中 `level` 屬性的值只是範例。</span><span class="sxs-lookup"><span data-stu-id="07e18-124">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="07e18-125">`uiAccess`預設為 "false";也就是說，如果省略屬性，或元件沒有資訊清單，應用程式將無法取得受保護 UI 的存取權。</span><span class="sxs-lookup"><span data-stu-id="07e18-125">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
