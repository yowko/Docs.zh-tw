---
title: WPF 主應用程式 (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: d3b1ebf3cd62b77a9082c0b149469462b5dffa3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577508"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="71b8d-102">WPF 主應用程式 (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="71b8d-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="71b8d-103">Windows Presentation Foundation (WPF) 主應用程式 (PresentationHost.exe) 是可讓應用程式[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]相容的瀏覽器中裝載應用程式 (包括[!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)]和更新版本)。</span><span class="sxs-lookup"><span data-stu-id="71b8d-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="71b8d-104">根據預設，Windows Presentation Foundation (WPF) 的主機已登錄的殼層並[!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)]處理常式，如瀏覽器裝載[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]內容，包括：</span><span class="sxs-lookup"><span data-stu-id="71b8d-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
-   <span data-ttu-id="71b8d-105">鬆散 (未編譯) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案 (.xaml)。</span><span class="sxs-lookup"><span data-stu-id="71b8d-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="71b8d-106">(.xbap)。</span><span class="sxs-lookup"><span data-stu-id="71b8d-106">(.xbap).</span></span>  
  
 <span data-ttu-id="71b8d-107">針對這些類型的檔案，Windows Presentation Foundation (WPF) 主機：</span><span class="sxs-lookup"><span data-stu-id="71b8d-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
-   <span data-ttu-id="71b8d-108">啟動已登錄[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]來裝載 Windows Presentation Foundation (WPF) 內容的處理常式。</span><span class="sxs-lookup"><span data-stu-id="71b8d-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
-   <span data-ttu-id="71b8d-109">載入所需的正確版本[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]和 Windows Presentation Foundation (WPF) 組件。</span><span class="sxs-lookup"><span data-stu-id="71b8d-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
-   <span data-ttu-id="71b8d-110">確保部署區域的適當權限等級都已就緒。</span><span class="sxs-lookup"><span data-stu-id="71b8d-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="71b8d-111">本主題說明可以搭配使用 PresentationHost.exe 的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="71b8d-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="71b8d-112">使用方式</span><span class="sxs-lookup"><span data-stu-id="71b8d-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="71b8d-113">參數</span><span class="sxs-lookup"><span data-stu-id="71b8d-113">Parameters</span></span>  
  
|<span data-ttu-id="71b8d-114">參數</span><span class="sxs-lookup"><span data-stu-id="71b8d-114">Parameter</span></span>|<span data-ttu-id="71b8d-115">描述</span><span class="sxs-lookup"><span data-stu-id="71b8d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71b8d-116">filename</span><span class="sxs-lookup"><span data-stu-id="71b8d-116">filename</span></span>|<span data-ttu-id="71b8d-117">要啟動的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="71b8d-117">The path of the file to be activated.</span></span> <span data-ttu-id="71b8d-118">也可以是 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71b8d-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="71b8d-119">-debug</span><span class="sxs-lookup"><span data-stu-id="71b8d-119">-debug</span></span>|<span data-ttu-id="71b8d-120">當啟動應用程式時，不會從存放區認可或執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="71b8d-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="71b8d-121">這只有在已啟動本機檔案時才有用。</span><span class="sxs-lookup"><span data-stu-id="71b8d-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="71b8d-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="71b8d-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="71b8d-123">可搭配 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 值使用，表示 PresentationHost.exe 應將應用程式視為已從指定 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 進行部署，並加以偵錯。</span><span class="sxs-lookup"><span data-stu-id="71b8d-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="71b8d-124">這會決定部署區域與原始站台。</span><span class="sxs-lookup"><span data-stu-id="71b8d-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="71b8d-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="71b8d-125">-embedding</span></span>|<span data-ttu-id="71b8d-126">為 OLE 的必要項。</span><span class="sxs-lookup"><span data-stu-id="71b8d-126">Required by OLE.</span></span> <span data-ttu-id="71b8d-127">如果已指定 `-event` 或 `-debug` 參數，就不需要指定 `-embedding` 參數，因為該參數已在內部設定。</span><span class="sxs-lookup"><span data-stu-id="71b8d-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="71b8d-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="71b8d-128">-event \<eventname></span></span>|<span data-ttu-id="71b8d-129">當 PresentationHost.exe 已初始化並準備好裝載 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 內容時，請開啟含此名稱的事件並對其發出通知。</span><span class="sxs-lookup"><span data-stu-id="71b8d-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="71b8d-130">如果開啟事件時發生錯誤 (例如事件尚未建立)，則會終止 PresentationHost.exe。</span><span class="sxs-lookup"><span data-stu-id="71b8d-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="71b8d-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="71b8d-131">-launchApplication \<url></span></span>|<span data-ttu-id="71b8d-132">從指定的 URL，啟動獨立 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="71b8d-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> <span data-ttu-id="71b8d-133">系統會套用與 .NET 應用程式相關的 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 和 WinINet 安全性原則。</span><span class="sxs-lookup"><span data-stu-id="71b8d-133">[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="71b8d-134">案例</span><span class="sxs-lookup"><span data-stu-id="71b8d-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="71b8d-135">殼層處理常式</span><span class="sxs-lookup"><span data-stu-id="71b8d-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="71b8d-136">MIME 處理常式</span><span class="sxs-lookup"><span data-stu-id="71b8d-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="71b8d-137">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="71b8d-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="71b8d-138">Visual Studio 區域中偵錯</span><span class="sxs-lookup"><span data-stu-id="71b8d-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="71b8d-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71b8d-139">See also</span></span>
- [<span data-ttu-id="71b8d-140">安全性</span><span class="sxs-lookup"><span data-stu-id="71b8d-140">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
