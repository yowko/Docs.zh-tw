---
title: WPF 主應用程式 (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: ec8ec42c174d87834af5d4c651c1e8c8bde3b3e2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581694"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="95721-102">WPF 主應用程式 (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="95721-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="95721-103">Windows Presentation Foundation （WPF）主機（Presentationhost.exe）是一種應用程式，可讓 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的應用程式裝載在相容的瀏覽器中（包括 Microsoft Internet Explorer 6 和更新版本）。</span><span class="sxs-lookup"><span data-stu-id="95721-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="95721-104">根據預設，Windows Presentation Foundation （WPF）主機會註冊為瀏覽器主控 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 內容的 shell 和 MIME 處理常式，其中包括：</span><span class="sxs-lookup"><span data-stu-id="95721-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="95721-105">鬆散 (未編譯) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案 (.xaml)。</span><span class="sxs-lookup"><span data-stu-id="95721-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="95721-106">(.xbap)。</span><span class="sxs-lookup"><span data-stu-id="95721-106">(.xbap).</span></span>  
  
 <span data-ttu-id="95721-107">對於這些類型的檔案，請 Windows Presentation Foundation （WPF）主機：</span><span class="sxs-lookup"><span data-stu-id="95721-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="95721-108">啟動已註冊的 HTML 處理常式，以裝載 Windows Presentation Foundation （WPF）內容。</span><span class="sxs-lookup"><span data-stu-id="95721-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="95721-109">載入所需 common language runtime （CLR）和 Windows Presentation Foundation （WPF）元件的正確版本。</span><span class="sxs-lookup"><span data-stu-id="95721-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="95721-110">確保部署區域的適當權限等級都已就緒。</span><span class="sxs-lookup"><span data-stu-id="95721-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="95721-111">本主題說明可以搭配使用 PresentationHost.exe 的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="95721-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="95721-112">使用量</span><span class="sxs-lookup"><span data-stu-id="95721-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="95721-113">參數</span><span class="sxs-lookup"><span data-stu-id="95721-113">Parameters</span></span>  
  
|<span data-ttu-id="95721-114">參數</span><span class="sxs-lookup"><span data-stu-id="95721-114">Parameter</span></span>|<span data-ttu-id="95721-115">描述</span><span class="sxs-lookup"><span data-stu-id="95721-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95721-116">filename</span><span class="sxs-lookup"><span data-stu-id="95721-116">filename</span></span>|<span data-ttu-id="95721-117">要啟動的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="95721-117">The path of the file to be activated.</span></span> <span data-ttu-id="95721-118">也可以是 URI。</span><span class="sxs-lookup"><span data-stu-id="95721-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="95721-119">-debug</span><span class="sxs-lookup"><span data-stu-id="95721-119">-debug</span></span>|<span data-ttu-id="95721-120">當啟動應用程式時，不會從存放區認可或執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="95721-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="95721-121">這只有在已啟動本機檔案時才有用。</span><span class="sxs-lookup"><span data-stu-id="95721-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="95721-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="95721-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="95721-123">與 URL 值搭配使用，以指示 Presentationhost.exe 應用程式應該進行調試，如同從指定的 URL 部署一樣。</span><span class="sxs-lookup"><span data-stu-id="95721-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="95721-124">這會決定部署區域與原始站台。</span><span class="sxs-lookup"><span data-stu-id="95721-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="95721-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="95721-125">-embedding</span></span>|<span data-ttu-id="95721-126">為 OLE 的必要項。</span><span class="sxs-lookup"><span data-stu-id="95721-126">Required by OLE.</span></span> <span data-ttu-id="95721-127">如果已指定 `-event` 或 `-debug` 參數，就不需要指定 `-embedding` 參數，因為該參數已在內部設定。</span><span class="sxs-lookup"><span data-stu-id="95721-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="95721-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="95721-128">-event \<eventname></span></span>|<span data-ttu-id="95721-129">當 PresentationHost.exe 已初始化並準備好裝載 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 內容時，請開啟含此名稱的事件並對其發出通知。</span><span class="sxs-lookup"><span data-stu-id="95721-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="95721-130">如果開啟事件時發生錯誤 (例如事件尚未建立)，則會終止 PresentationHost.exe。</span><span class="sxs-lookup"><span data-stu-id="95721-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="95721-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="95721-131">-launchApplication \<url></span></span>|<span data-ttu-id="95721-132">從指定的 URL 啟動獨立 ClickOnce 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95721-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="95721-133">適用于 .NET 應用程式的 Internet Explorer 和 WinINet 安全性原則會套用。</span><span class="sxs-lookup"><span data-stu-id="95721-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="95721-134">案例</span><span class="sxs-lookup"><span data-stu-id="95721-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="95721-135">殼層處理常式</span><span class="sxs-lookup"><span data-stu-id="95721-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="95721-136">MIME 處理常式</span><span class="sxs-lookup"><span data-stu-id="95721-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="95721-137">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="95721-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="95721-138">Visual Studio 區域中偵錯</span><span class="sxs-lookup"><span data-stu-id="95721-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="95721-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="95721-139">See also</span></span>

- [<span data-ttu-id="95721-140">Security</span><span class="sxs-lookup"><span data-stu-id="95721-140">Security</span></span>](../security-wpf.md)
