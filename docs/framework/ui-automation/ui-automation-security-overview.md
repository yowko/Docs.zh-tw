---
title: UI 自動化安全性概觀
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 926fed8b2f03e90fd3ccf85564a20ff7b2a7d687
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674376"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="49920-102">UI 自動化安全性概觀</span><span class="sxs-lookup"><span data-stu-id="49920-102">UI Automation Security Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="49920-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="49920-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="49920-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="49920-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="49920-105">本概觀說明 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 中 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="49920-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a><span data-ttu-id="49920-106">使用者帳戶控制</span><span class="sxs-lookup"><span data-stu-id="49920-106">User Account Control</span></span>  
 <span data-ttu-id="49920-107">安全性是 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] 的主要焦點，在所有創新功能中，這項功能可以讓使用者以標準 (非系統管理員) 使用者身分執行，但不會被封鎖而無法執行需要更高權限的應用程式和服務。</span><span class="sxs-lookup"><span data-stu-id="49920-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>  
  
 <span data-ttu-id="49920-108">在 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]中，大部分的應用程式都具備標準或系統管理語彙基元。</span><span class="sxs-lookup"><span data-stu-id="49920-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="49920-109">如果無法將應用程式識別為系統管理應用程式，根據預設，它就會啟動為標準應用程式。</span><span class="sxs-lookup"><span data-stu-id="49920-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="49920-110">識別為系統管理的應用程式啟動之前， [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] 會提示使用者是否同意以提高權限的方式執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="49920-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="49920-111">即使使用者是本機 Administrators 群組的成員，預設也會顯示同意提示，因為在需要管理認證的應用程式或系統元件要求執行權限之前，系統管理員會以標準使用者身分執行。</span><span class="sxs-lookup"><span data-stu-id="49920-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="49920-112">需要更高權限的工作</span><span class="sxs-lookup"><span data-stu-id="49920-112">Tasks Requiring Higher Privileges</span></span>  
 <span data-ttu-id="49920-113">當使用者嘗試執行需要系統管理權限的工作時， [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] 會顯示對話方塊，詢問使用者是否同意繼續進行。</span><span class="sxs-lookup"><span data-stu-id="49920-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="49920-114">這個對話方塊會防止跨處理序通訊的存取，因此惡意軟體無法模擬使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="49920-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="49920-115">同樣地，其他處理序通常也無法存取桌面登入畫面。</span><span class="sxs-lookup"><span data-stu-id="49920-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>  
  
 <span data-ttu-id="49920-116">使用者介面自動化用戶端必須與其他處理序通訊，其中部分可能會以更高的權限層級執行。</span><span class="sxs-lookup"><span data-stu-id="49920-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="49920-117">用戶端也可能需要存取一般不會對其他處理序顯示的系統對話方塊。</span><span class="sxs-lookup"><span data-stu-id="49920-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="49920-118">因此， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 用戶端必須受系統信任，而且必須以特殊權限執行。</span><span class="sxs-lookup"><span data-stu-id="49920-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>  
  
 <span data-ttu-id="49920-119">若要受信任以便與以較高權限層級執行的應用程式通訊，必須簽署應用程式。</span><span class="sxs-lookup"><span data-stu-id="49920-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a><span data-ttu-id="49920-120">資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="49920-120">Manifest Files</span></span>  
 <span data-ttu-id="49920-121">若要取得對受保護系統 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]的存取權，應用程式在建立時必須含有資訊清單檔，且該資訊清單檔中必須含有特殊屬性。</span><span class="sxs-lookup"><span data-stu-id="49920-121">To gain access to the protected system [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], applications must be built with a manifest file that includes a special attribute in the manifest file.</span></span> <span data-ttu-id="49920-122">這個 `uiAccess` 屬性包含在 `requestedExecutionLevel` 標記中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="49920-122">This `uiAccess` attribute is included in the `requestedExecutionLevel` tag, as follows:</span></span>  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 <span data-ttu-id="49920-123">這個程式碼中 `level` 屬性的值只是範例。</span><span class="sxs-lookup"><span data-stu-id="49920-123">The value of the `level` attribute in this code is an example only.</span></span>  
  
 <span data-ttu-id="49920-124">`UIAccess` 預設為 "false"；也就是說，如果省略這個屬性，或者組件沒有資訊清單，應用程式就無法取得受保護的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]的存取權。</span><span class="sxs-lookup"><span data-stu-id="49920-124">`UIAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="49920-125">如需詳細資訊[!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)]安全性、 簽署應用程式和建立組件資訊清單，請參閱[開發人員最佳實務和最低權限環境中的應用程式的指導方針](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480150(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="49920-125">For more information on [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] security, on signing applications, and on creating assembly manifests, see [Developer Best Practices and Guidelines for Applications in a Least Privileged Environment](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480150(v=msdn.10)).</span></span>
