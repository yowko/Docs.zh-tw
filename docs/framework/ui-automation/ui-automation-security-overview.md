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
# <a name="ui-automation-security-overview"></a><span data-ttu-id="d031f-102">UI 自動化安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d031f-102">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="d031f-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="d031f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d031f-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="d031f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="d031f-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="d031f-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="d031f-106">使用者帳戶控制</span><span class="sxs-lookup"><span data-stu-id="d031f-106">User Account Control</span></span>

<span data-ttu-id="d031f-107">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span><span class="sxs-lookup"><span data-stu-id="d031f-107">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="d031f-108">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span><span class="sxs-lookup"><span data-stu-id="d031f-108">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="d031f-109">如果無法將應用程式識別為系統管理應用程式，根據預設，它就會啟動為標準應用程式。</span><span class="sxs-lookup"><span data-stu-id="d031f-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="d031f-110">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span><span class="sxs-lookup"><span data-stu-id="d031f-110">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="d031f-111">即使使用者是本機 Administrators 群組的成員，預設也會顯示同意提示，因為在需要管理認證的應用程式或系統元件要求執行權限之前，系統管理員會以標準使用者身分執行。</span><span class="sxs-lookup"><span data-stu-id="d031f-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="d031f-112">需要更高權限的工作</span><span class="sxs-lookup"><span data-stu-id="d031f-112">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="d031f-113">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span><span class="sxs-lookup"><span data-stu-id="d031f-113">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="d031f-114">這個對話方塊會防止跨處理序通訊的存取，因此惡意軟體無法模擬使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="d031f-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="d031f-115">同樣地，其他處理序通常也無法存取桌面登入畫面。</span><span class="sxs-lookup"><span data-stu-id="d031f-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="d031f-116">使用者介面自動化用戶端必須與其他處理序通訊，其中部分可能會以更高的權限層級執行。</span><span class="sxs-lookup"><span data-stu-id="d031f-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="d031f-117">用戶端也可能需要存取一般不會對其他處理序顯示的系統對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d031f-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="d031f-118">因此， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 用戶端必須受系統信任，而且必須以特殊權限執行。</span><span class="sxs-lookup"><span data-stu-id="d031f-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="d031f-119">若要受信任以便與以較高權限層級執行的應用程式通訊，必須簽署應用程式。</span><span class="sxs-lookup"><span data-stu-id="d031f-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="d031f-120">資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="d031f-120">Manifest Files</span></span>

<span data-ttu-id="d031f-121">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span><span class="sxs-lookup"><span data-stu-id="d031f-121">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

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

<span data-ttu-id="d031f-122">這個程式碼中 `level` 屬性的值只是範例。</span><span class="sxs-lookup"><span data-stu-id="d031f-122">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="d031f-123">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span><span class="sxs-lookup"><span data-stu-id="d031f-123">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
