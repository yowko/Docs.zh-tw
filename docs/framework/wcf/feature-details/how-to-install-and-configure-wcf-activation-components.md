---
title: "HOW TO：安裝和設定 WCF 啟用元件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77dec85ee12250080fc487d120749892a148ef17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="b4e47-102">HOW TO：安裝和設定 WCF 啟用元件</span><span class="sxs-lookup"><span data-stu-id="b4e47-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="b4e47-103">本主題說明設定 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中 Windows Process Activation Service (亦稱為 WAS) 來裝載無法透過 HTTP 網路通訊協定進行通訊的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="b4e47-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="b4e47-104">下列各節將概述此組態的各項步驟：</span><span class="sxs-lookup"><span data-stu-id="b4e47-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="b4e47-105">安裝 (或確認安裝) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動元件。</span><span class="sxs-lookup"><span data-stu-id="b4e47-105">Install (or confirm the installation of) the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activation components.</span></span>  
  
-   <span data-ttu-id="b4e47-106">設定 WAS 支援非 HTTP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="b4e47-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="b4e47-107">下列程序將設定 [!INCLUDE[wv](../../../../includes/wv-md.md)] 以啟動 TCP。</span><span class="sxs-lookup"><span data-stu-id="b4e47-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="b4e47-108">安裝和設定 WAS，請參閱之後[如何： 將 WCF 服務裝載於 WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)程序來建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]公開非 HTTP 端點採用 WAS 的服務。</span><span class="sxs-lookup"><span data-stu-id="b4e47-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="b4e47-109">若要安裝 WCF 非 HTTP 啟動元件</span><span class="sxs-lookup"><span data-stu-id="b4e47-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="b4e47-110">按一下**啟動**按鈕，然後再按一下**控制台**。</span><span class="sxs-lookup"><span data-stu-id="b4e47-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="b4e47-111">按一下**程式**，然後按一下 **程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="b4e47-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="b4e47-112">在**工作**功能表上，按一下 **開啟或關閉 Windows 功能**。</span><span class="sxs-lookup"><span data-stu-id="b4e47-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="b4e47-113">找出並選取 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 節點，然後將它展開。</span><span class="sxs-lookup"><span data-stu-id="b4e47-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="b4e47-114">選取**WCF 非 Http 啟動元件**方塊，然後儲存設定。</span><span class="sxs-lookup"><span data-stu-id="b4e47-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="b4e47-115">若要設定 WAS 來支援 TCP 啟動</span><span class="sxs-lookup"><span data-stu-id="b4e47-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="b4e47-116">若要支援 net.tcp 啟動，預設的網站必須先繫結至 net.tcp 連接埠。</span><span class="sxs-lookup"><span data-stu-id="b4e47-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="b4e47-117">您可以使用與 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 管理工具集一起安裝的 Appcmd.exe 完成此操作。</span><span class="sxs-lookup"><span data-stu-id="b4e47-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="b4e47-118">從系統管理員層級的 [命令提示字元] 視窗中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b4e47-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b4e47-119">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="b4e47-119">This command is a single line of text.</span></span> <span data-ttu-id="b4e47-120">此命令會將 net.tcp 網站繫結新增至使用任何主機名稱來接聽 TCP 連接埠編號 808 的預設網站。</span><span class="sxs-lookup"><span data-stu-id="b4e47-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="b4e47-121">雖然網站中的所有應用程式共用常見的 net.tcp 繫結，但每個應用程式都可以個別啟用 net.tcp 支援。</span><span class="sxs-lookup"><span data-stu-id="b4e47-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="b4e47-122">若要啟用應用程式的 net.tcp，請從系統管理員層級的命令提示字元中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b4e47-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b4e47-123">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="b4e47-123">This command is a single line of text.</span></span> <span data-ttu-id="b4e47-124">此命令會啟用 /\<*WCF 應用程式*> 應用程式使用這兩個 http://localhost 存取*/\<WCF 應用程式 >*和 net.tcp://localhost /*\<WCF 應用程式 >*。</span><span class="sxs-lookup"><span data-stu-id="b4e47-124">This command enables the /\<*WCF Application*> application to be accessed using both http://localhost*/\<WCF Application>* and net.tcp://localhost/*\<WCF Application>*.</span></span>  
  
     <span data-ttu-id="b4e47-125">移除您為此範例新增的 net.tcp 網站繫結。</span><span class="sxs-lookup"><span data-stu-id="b4e47-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="b4e47-126">為了方便起見，下列兩個步驟會以範例目錄中名為 RemoveNetTcpSiteBinding.cmd 的批次檔來加以實作。</span><span class="sxs-lookup"><span data-stu-id="b4e47-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="b4e47-127">透過系統管理員層級的 [命令提示字元] 視窗執行下列命令，以從啟用的通訊協定清單中移除 net.tcp。</span><span class="sxs-lookup"><span data-stu-id="b4e47-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="b4e47-128">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="b4e47-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="b4e47-129">從提高權限的 [命令提示字元] 視窗中執行下列命令以移除 net.tcp 網站繫結：</span><span class="sxs-lookup"><span data-stu-id="b4e47-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="b4e47-130">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="b4e47-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="b4e47-131">若要從啟用的通訊協定清單中移除 net.tcp</span><span class="sxs-lookup"><span data-stu-id="b4e47-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="b4e47-132">若要從啟用的通訊協定清單中移除 net.tcp，請透過系統管理員層級的 [命令提示字元] 視窗執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b4e47-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b4e47-133">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="b4e47-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="b4e47-134">若要移除 net.tcp 網站繫結</span><span class="sxs-lookup"><span data-stu-id="b4e47-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="b4e47-135">若要移除 net.tcp 網站繫結，請透過系統管理員層級的 [命令提示字元] 視窗執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b4e47-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b4e47-136">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="b4e47-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e47-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4e47-137">See Also</span></span>  
 [<span data-ttu-id="b4e47-138">TCP 啟動</span><span class="sxs-lookup"><span data-stu-id="b4e47-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="b4e47-139">MSMQ 啟用</span><span class="sxs-lookup"><span data-stu-id="b4e47-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="b4e47-140">NamedPipe 啟用</span><span class="sxs-lookup"><span data-stu-id="b4e47-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="b4e47-141">Windows Server App Fabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="b4e47-141">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
