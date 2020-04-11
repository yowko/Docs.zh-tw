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
# <a name="troubleshoot-setup-issues"></a>排除設定問題

本文介紹如何解決 Windows 通信基礎 (WCF) 設置問題。  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>有些 Windows Communication Foundation 登錄機碼 (Registry Key) 無法藉由在 .NET Framework 3.0 上執行 MSI 修復作業來加以修復。  
 如果您刪除下列任何登錄機碼：  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 如果使用從**控制面板**中的 **「添加/刪除程式**」小程式啟動的 .NET 框架 3.0 安裝程式執行修復,則不會重新建立金鑰。 若要正確地重新建立這些機碼，使用者必須解除安裝並重新安裝 .NET Framework 3.0。  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>WMI 服務損毀在 .NET Framework 3.0 套件安裝期間封鎖 Windows Communication Foundation WMI 提供者的安裝  
 WMI 服務損毀可能會封鎖 Windows Communication Foundation WMI 提供者的安裝。 在進行安裝時，Windows Communication Foundation 安裝程式無法使用 mofcomp.exe 元件來註冊 WCF .mof 檔。 可能徵兆如下所示：  
  
1. .NET Framework 3.0 安裝成功完成，不過 WCF WMI 提供者並未註冊。  
  
2. 應用程式記錄檔中顯示關於在註冊 WCF 的 WMI 提供者、或執行 mofcomp.exe 時所發生問題的錯誤事件。  
  
3. 在使用者的 %temp% 目錄中名為 dd_wcf_retCA* 的安裝記錄檔，包含了無法註冊 WCF WMI 提供者的相關資訊。  
  
4. 在事件記錄檔或安裝追蹤記錄檔中，可能會列出下列其中一個例外狀況 (Exception)：  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: 以 "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" 執行 E:\WINDOWS\system32\wbem\mofcomp.exe 時產生未預期的結果 3  
  
     或者：  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: 'System.Management.ManagementPath' 的型別初始設定式發生例外狀況。 --->系统.Runtime.InteropServices.COMexception (0x80040154):檢索 CLSID [CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA] 的元件的 COM 類工廠,由於以下錯誤:80040154。  
  
     或者：  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: 無法載入檔案或組件 'C:\WINDOWS\system32\wbem\mofcomp.exe' 或其相依性的其中之一。 系統找不到指定的檔案。  
  
     檔案名稱：'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 您必須遵循下列步驟才能解決上述問題。  
  
1. 運行[WMI 診斷實用程式](https://www.microsoft.com/download/details.aspx?id=7684)以修復 WMI 服務。 有關使用此工具的詳細資訊,請參閱[WMI 診斷實用程式](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10))。  
  
 使用**位於控制面板**中的 **「添加/刪除程式**」小程式,或卸載/重新安裝 .NET 框架 3.0 來修復 .NET 框架 3.0 安裝。  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>在安裝 .NET Framework 3.5 後修復 .NET Framework 3.0 會將 machine.config 中由 .NET Framework 3.5 引入的組態項目移除  
 如果在安裝 .NET 框架 3.5 後對 .NET 框架 3.0 進行了修復,則將刪除機器中的 .NET Framework 3.5 引入的配置項目。 不過，web.config 會保持不變。 解決方法是通過 ARP 在此之後修復 .NET 框架 3.5,或使用隨`/c`交換機執行[工作流服務註冊工具 (WF ServicesReg.exe)。](workflow-service-registration-tool-wfservicesreg-exe.md)  
  
 [工作流服務註冊工具 (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md)可在 %windir%\Microsoft.NET_framework_v3.5] 或 %windir%_Microsoft.NET_framework64_v3.5] 找到。  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>在安裝 .NET Framework 3.5 之後，適當地為 WCF/WF Webhost 設定 IIS  
 當 .NET Framework 3.5 安裝無法配置其他與 WCF 相關的 IIS 配置設置時,它將記錄安裝日誌中的錯誤並繼續。 任何執行 WorkflowServices 應用程式的嘗試都將失敗，因為缺少必要的組態設定。 例如，無法載入 xoml 或規則服務。  
  
 要解決此問題,請使用帶有`/c`交換機的[工作流服務註冊工具 (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md)在電腦上正確配置 IIS 文本映射。 [工作流服務註冊工具 (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md)可在 %windir%\Microsoft.NET_framework_v3.5] 或 %windir%_Microsoft.NET_framework64_v3.5] 找到。  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>無法載入程式集"System.ServiceModel,啟動.HTTPModule"從程式集"System.ServiceModel,版本 3.0.0.0,區域性_中性,公共密鑰令牌_b77a5c561934e089"  
 如果安裝了 .NET 框架 4,然後啟用了 WCF HTTP 啟動,則會發生此錯誤。 要解決此問題,請將以下命令行從可視化工作室的開發人員命令提示符中運行:  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>另請參閱

- [設定說明](./samples/set-up-instructions.md)
