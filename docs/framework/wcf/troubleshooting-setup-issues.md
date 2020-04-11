---
title: 疑難排解安裝程式問題
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 2cd9ced4f0780b1a6f63e4a5833e20ac91870121
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121586"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="f0aba-102">排除設定問題</span><span class="sxs-lookup"><span data-stu-id="f0aba-102">Troubleshoot setup issues</span></span>

<span data-ttu-id="f0aba-103">本文介紹如何解決 Windows 通信基礎 (WCF) 設置問題。</span><span class="sxs-lookup"><span data-stu-id="f0aba-103">This article describes how to troubleshoot Windows Communication Foundation (WCF) set up issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="f0aba-104">有些 Windows Communication Foundation 登錄機碼 (Registry Key) 無法藉由在 .NET Framework 3.0 上執行 MSI 修復作業來加以修復。</span><span class="sxs-lookup"><span data-stu-id="f0aba-104">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  
 <span data-ttu-id="f0aba-105">如果您刪除下列任何登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="f0aba-105">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="f0aba-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="f0aba-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="f0aba-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="f0aba-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="f0aba-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="f0aba-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="f0aba-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="f0aba-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="f0aba-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="f0aba-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="f0aba-111">如果使用從**控制面板**中的 **「添加/刪除程式**」小程式啟動的 .NET 框架 3.0 安裝程式執行修復,則不會重新建立金鑰。</span><span class="sxs-lookup"><span data-stu-id="f0aba-111">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="f0aba-112">若要正確地重新建立這些機碼，使用者必須解除安裝並重新安裝 .NET Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="f0aba-112">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a><span data-ttu-id="f0aba-113">WMI 服務損毀在 .NET Framework 3.0 套件安裝期間封鎖 Windows Communication Foundation WMI 提供者的安裝</span><span class="sxs-lookup"><span data-stu-id="f0aba-113">WMI Service Corruption Blocks Installation of the Windows Communication Foundation WMI provider during installation of .NET Framework 3.0 package</span></span>  
 <span data-ttu-id="f0aba-114">WMI 服務損毀可能會封鎖 Windows Communication Foundation WMI 提供者的安裝。</span><span class="sxs-lookup"><span data-stu-id="f0aba-114">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider.</span></span> <span data-ttu-id="f0aba-115">在進行安裝時，Windows Communication Foundation 安裝程式無法使用 mofcomp.exe 元件來註冊 WCF .mof 檔。</span><span class="sxs-lookup"><span data-stu-id="f0aba-115">During installation the Windows Communication Foundation installer is unable to register the WCF .mof file using the mofcomp.exe component.</span></span> <span data-ttu-id="f0aba-116">可能徵兆如下所示：</span><span class="sxs-lookup"><span data-stu-id="f0aba-116">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="f0aba-117">.NET Framework 3.0 安裝成功完成，不過 WCF WMI 提供者並未註冊。</span><span class="sxs-lookup"><span data-stu-id="f0aba-117">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="f0aba-118">應用程式記錄檔中顯示關於在註冊 WCF 的 WMI 提供者、或執行 mofcomp.exe 時所發生問題的錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="f0aba-118">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="f0aba-119">在使用者的 %temp% 目錄中名為 dd_wcf_retCA\* 的安裝記錄檔，包含了無法註冊 WCF WMI 提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f0aba-119">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="f0aba-120">在事件記錄檔或安裝追蹤記錄檔中，可能會列出下列其中一個例外狀況 (Exception)：</span><span class="sxs-lookup"><span data-stu-id="f0aba-120">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="f0aba-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: 以 "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" 執行 E:\WINDOWS\system32\wbem\mofcomp.exe 時產生未預期的結果 3</span><span class="sxs-lookup"><span data-stu-id="f0aba-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="f0aba-122">或者：</span><span class="sxs-lookup"><span data-stu-id="f0aba-122">or:</span></span>  
  
     <span data-ttu-id="f0aba-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: 'System.Management.ManagementPath' 的型別初始設定式發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0aba-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="f0aba-124">--->系统.Runtime.InteropServices.COMexception (0x80040154):檢索 CLSID [CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA] 的元件的 COM 類工廠,由於以下錯誤:80040154。</span><span class="sxs-lookup"><span data-stu-id="f0aba-124">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="f0aba-125">或者：</span><span class="sxs-lookup"><span data-stu-id="f0aba-125">or:</span></span>  
  
     <span data-ttu-id="f0aba-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: 無法載入檔案或組件 'C:\WINDOWS\system32\wbem\mofcomp.exe' 或其相依性的其中之一。</span><span class="sxs-lookup"><span data-stu-id="f0aba-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="f0aba-127">系統找不到指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="f0aba-127">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="f0aba-128">檔案名稱：'C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="f0aba-128">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="f0aba-129">您必須遵循下列步驟才能解決上述問題。</span><span class="sxs-lookup"><span data-stu-id="f0aba-129">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="f0aba-130">運行[WMI 診斷實用程式](https://www.microsoft.com/download/details.aspx?id=7684)以修復 WMI 服務。</span><span class="sxs-lookup"><span data-stu-id="f0aba-130">Run the [WMI Diagnosis Utility](https://www.microsoft.com/download/details.aspx?id=7684) to repair the WMI service.</span></span> <span data-ttu-id="f0aba-131">有關使用此工具的詳細資訊,請參閱[WMI 診斷實用程式](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10))。</span><span class="sxs-lookup"><span data-stu-id="f0aba-131">For more information about using this tool, see [WMI Diagnosis Utility](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="f0aba-132">使用**位於控制面板**中的 **「添加/刪除程式**」小程式,或卸載/重新安裝 .NET 框架 3.0 來修復 .NET 框架 3.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="f0aba-132">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a><span data-ttu-id="f0aba-133">在安裝 .NET Framework 3.5 後修復 .NET Framework 3.0 會將 machine.config 中由 .NET Framework 3.5 引入的組態項目移除</span><span class="sxs-lookup"><span data-stu-id="f0aba-133">Repairing .NET Framework 3.0 after .NET Framework 3.5 Installation Removes Configuration Elements Introduced by .NET Framework 3.5 in machine.config</span></span>  
 <span data-ttu-id="f0aba-134">如果在安裝 .NET 框架 3.5 後對 .NET 框架 3.0 進行了修復,則將刪除機器中的 .NET Framework 3.5 引入的配置項目。</span><span class="sxs-lookup"><span data-stu-id="f0aba-134">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in machine.config are removed.</span></span> <span data-ttu-id="f0aba-135">不過，web.config 會保持不變。</span><span class="sxs-lookup"><span data-stu-id="f0aba-135">However, the web.config remains intact.</span></span> <span data-ttu-id="f0aba-136">解決方法是通過 ARP 在此之後修復 .NET 框架 3.5,或使用隨`/c`交換機執行[工作流服務註冊工具 (WF ServicesReg.exe)。](workflow-service-registration-tool-wfservicesreg-exe.md)</span><span class="sxs-lookup"><span data-stu-id="f0aba-136">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="f0aba-137">[工作流服務註冊工具 (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md)可在 %windir%\Microsoft.NET_framework_v3.5] 或 %windir%_Microsoft.NET_framework64_v3.5] 找到。</span><span class="sxs-lookup"><span data-stu-id="f0aba-137">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="f0aba-138">在安裝 .NET Framework 3.5 之後，適當地為 WCF/WF Webhost 設定 IIS</span><span class="sxs-lookup"><span data-stu-id="f0aba-138">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  
 <span data-ttu-id="f0aba-139">當 .NET Framework 3.5 安裝無法配置其他與 WCF 相關的 IIS 配置設置時,它將記錄安裝日誌中的錯誤並繼續。</span><span class="sxs-lookup"><span data-stu-id="f0aba-139">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="f0aba-140">任何執行 WorkflowServices 應用程式的嘗試都將失敗，因為缺少必要的組態設定。</span><span class="sxs-lookup"><span data-stu-id="f0aba-140">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="f0aba-141">例如，無法載入 xoml 或規則服務。</span><span class="sxs-lookup"><span data-stu-id="f0aba-141">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="f0aba-142">要解決此問題,請使用帶有`/c`交換機的[工作流服務註冊工具 (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md)在電腦上正確配置 IIS 文本映射。</span><span class="sxs-lookup"><span data-stu-id="f0aba-142">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="f0aba-143">[工作流服務註冊工具 (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md)可在 %windir%\Microsoft.NET_framework_v3.5] 或 %windir%_Microsoft.NET_framework64_v3.5] 找到。</span><span class="sxs-lookup"><span data-stu-id="f0aba-143">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a><span data-ttu-id="f0aba-144">無法載入程式集"System.ServiceModel,啟動.HTTPModule"從程式集"System.ServiceModel,版本 3.0.0.0,區域性_中性,公共密鑰令牌_b77a5c561934e089"</span><span class="sxs-lookup"><span data-stu-id="f0aba-144">Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'</span></span>  
 <span data-ttu-id="f0aba-145">如果安裝了 .NET 框架 4,然後啟用了 WCF HTTP 啟動,則會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0aba-145">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="f0aba-146">要解決此問題,請將以下命令行從可視化工作室的開發人員命令提示符中運行:</span><span class="sxs-lookup"><span data-stu-id="f0aba-146">To resolve the issue run the following command-line from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0aba-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0aba-147">See also</span></span>

- [<span data-ttu-id="f0aba-148">設定說明</span><span class="sxs-lookup"><span data-stu-id="f0aba-148">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
