---
title: 疑難排解安裝程式問題
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 596aae345061796535895a091c59d50a5bffe0d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255113"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="4a1fa-102">針對安裝問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="4a1fa-102">Troubleshoot setup issues</span></span>

<span data-ttu-id="4a1fa-103">本文說明如何針對 Windows Communication Foundation (WCF) 安裝程式問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-103">This article describes how to troubleshoot Windows Communication Foundation (WCF) setup issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="4a1fa-104">有些 Windows Communication Foundation 登錄機碼 (Registry Key) 無法藉由在 .NET Framework 3.0 上執行 MSI 修復作業來加以修復。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-104">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  

 <span data-ttu-id="4a1fa-105">如果您刪除下列任何登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="4a1fa-105">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="4a1fa-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="4a1fa-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="4a1fa-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="4a1fa-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="4a1fa-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="4a1fa-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="4a1fa-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="4a1fa-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="4a1fa-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="4a1fa-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="4a1fa-111">如果您使用從 **主控台** 中的 [**新增/移除程式**] 小程式啟動的 .NET Framework 3.0 安裝程式來執行修復，則不會重新建立金鑰。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-111">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="4a1fa-112">若要正確地重新建立這些機碼，使用者必須解除安裝並重新安裝 .NET Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-112">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a><span data-ttu-id="4a1fa-113">WMI 服務損毀封鎖 WMI 提供者的安裝</span><span class="sxs-lookup"><span data-stu-id="4a1fa-113">WMI Service Corruption Blocks Installation of the WMI provider</span></span>

 <span data-ttu-id="4a1fa-114">WMI 服務損毀可能會在安裝 .NET Framework 3.0 套件時封鎖 Windows Communication Foundation WMI 提供者的安裝。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-114">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider when installing the .NET Framework 3.0 package.</span></span> <span data-ttu-id="4a1fa-115">在安裝期間，Windows Communication Foundation 安裝程式無法使用 *mofcomp.exe* 元件註冊 WCF *. mof* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-115">During installation, the Windows Communication Foundation installer is unable to register the WCF *.mof* file using the *mofcomp.exe* component.</span></span> <span data-ttu-id="4a1fa-116">可能徵兆如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a1fa-116">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="4a1fa-117">.NET Framework 3.0 安裝成功完成，不過 WCF WMI 提供者並未註冊。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-117">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="4a1fa-118">應用程式記錄檔中顯示關於在註冊 WCF 的 WMI 提供者、或執行 mofcomp.exe 時所發生問題的錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-118">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="4a1fa-119">在使用者的 %temp% 目錄中名為 dd_wcf_retCA\* 的安裝記錄檔，包含了無法註冊 WCF WMI 提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-119">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="4a1fa-120">在事件記錄檔或安裝追蹤記錄檔中，可能會列出下列其中一個例外狀況 (Exception)：</span><span class="sxs-lookup"><span data-stu-id="4a1fa-120">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="4a1fa-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: 以 "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" 執行 E:\WINDOWS\system32\wbem\mofcomp.exe 時產生未預期的結果 3</span><span class="sxs-lookup"><span data-stu-id="4a1fa-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="4a1fa-122">或者：</span><span class="sxs-lookup"><span data-stu-id="4a1fa-122">or:</span></span>  
  
     <span data-ttu-id="4a1fa-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: 'System.Management.ManagementPath' 的型別初始設定式發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="4a1fa-124">---> System.runtime.interopservices.outattribute. COMException (0x80040154) ：為 CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} 的元件抓取 COM class factory 失敗，因為發生下列錯誤：80040154。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-124">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="4a1fa-125">或者：</span><span class="sxs-lookup"><span data-stu-id="4a1fa-125">or:</span></span>  
  
     <span data-ttu-id="4a1fa-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: 無法載入檔案或組件 'C:\WINDOWS\system32\wbem\mofcomp.exe' 或其相依性的其中之一。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="4a1fa-127">系統找不到指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-127">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="4a1fa-128">檔案名稱：'C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="4a1fa-128">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="4a1fa-129">您必須遵循下列步驟才能解決上述問題。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-129">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="4a1fa-130">執行 WMI Diagnosis Utility 以修復 WMI 服務。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-130">Run the WMI Diagnosis Utility to repair the WMI service.</span></span> <span data-ttu-id="4a1fa-131">如需使用此工具的詳細資訊，請參閱 [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10))。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-131">For more information about using this tool, see [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="4a1fa-132">使用位於 **主控台** 中的 [**新增/移除程式**] 小程式，或卸載/重新安裝 .NET Framework 3.0，以修復 .NET Framework 3.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-132">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a><span data-ttu-id="4a1fa-133">在 .NET Framework 3.5 安裝之後修復 .NET Framework 3。0</span><span class="sxs-lookup"><span data-stu-id="4a1fa-133">Repair .NET Framework 3.0 after .NET Framework 3.5 Installation</span></span>

 <span data-ttu-id="4a1fa-134">如果您在安裝 .NET Framework 3.5 之後修復 .NET Framework 3.0，則會移除 *machine.config* 中 .NET Framework 3.5 所引進的設定元素。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-134">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in *machine.config* are removed.</span></span> <span data-ttu-id="4a1fa-135">不過， *web.config* 檔案會保持不變。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-135">However, the *web.config* file remains intact.</span></span> <span data-ttu-id="4a1fa-136">因應措施是透過 ARP 來修復 .NET Framework 3.5，或使用 [工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) 搭配 `/c` 參數。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-136">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="4a1fa-137">您可以在%windir%\Microsoft.NET\framework\v3.5\ 或%windir%\Microsoft.NET\framework64\v3.5\ 找到[工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md)</span><span class="sxs-lookup"><span data-stu-id="4a1fa-137">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="4a1fa-138">在安裝 .NET Framework 3.5 之後，適當地為 WCF/WF Webhost 設定 IIS</span><span class="sxs-lookup"><span data-stu-id="4a1fa-138">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  

 <span data-ttu-id="4a1fa-139">當 .NET Framework 3.5 安裝無法設定其他與 WCF 相關的 IIS 設定時，它會在安裝記錄檔中記錄錯誤，並繼續進行。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-139">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="4a1fa-140">任何執行 WorkflowServices 應用程式的嘗試都將失敗，因為缺少必要的組態設定。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-140">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="4a1fa-141">例如，無法載入 xoml 或規則服務。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-141">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="4a1fa-142">若要解決這個問題，請使用 [工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) 搭配 `/c` 參數，以在電腦上正確設定 IIS 腳本對應。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-142">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="4a1fa-143">您可以在%windir%\Microsoft.NET\framework\v3.5\ 或%windir%\Microsoft.NET\framework64\v3.5\ 找到[工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md)</span><span class="sxs-lookup"><span data-stu-id="4a1fa-143">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a><span data-ttu-id="4a1fa-144">無法載入類型 ' HttpModule '</span><span class="sxs-lookup"><span data-stu-id="4a1fa-144">Could not load type 'System.ServiceModel.Activation.HttpModule'</span></span>

<span data-ttu-id="4a1fa-145">**無法從元件 ' System.servicemodel，Version 3.0.0.0，Culture = 中性，PublicKeyToken = b77a5c561934e089 ' 載入類型 ' HttpModule '**</span><span class="sxs-lookup"><span data-stu-id="4a1fa-145">**Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'**</span></span>

 <span data-ttu-id="4a1fa-146">如果已安裝 .NET Framework 4，然後啟用 WCF HTTP 啟用，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a1fa-146">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="4a1fa-147">若要解決此問題，請從開發人員命令提示字元內部執行下列命令，以進行 Visual Studio：</span><span class="sxs-lookup"><span data-stu-id="4a1fa-147">To resolve the issue, run the following command from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a1fa-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a1fa-148">See also</span></span>

- [<span data-ttu-id="4a1fa-149">設定指示</span><span class="sxs-lookup"><span data-stu-id="4a1fa-149">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
