---
title: 疑難排解安裝程式問題
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: fb687e9975ab9ac763030f10d54c7744dc02c9e0
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720448"
---
# <a name="troubleshoot-setup-issues"></a>針對安裝問題進行疑難排解

本文說明如何針對 Windows Communication Foundation (WCF) 安裝程式問題進行疑難排解。  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>有些 Windows Communication Foundation 登錄機碼 (Registry Key) 無法藉由在 .NET Framework 3.0 上執行 MSI 修復作業來加以修復。  
 如果您刪除下列任何登錄機碼：  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 如果您使用從**主控台**中的 [**新增/移除程式**] 小程式啟動的 .NET Framework 3.0 安裝程式來執行修復，則不會重新建立金鑰。 若要正確地重新建立這些機碼，使用者必須解除安裝並重新安裝 .NET Framework 3.0。  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a>WMI 服務損毀封鎖 WMI 提供者的安裝

 WMI 服務損毀可能會在安裝 .NET Framework 3.0 套件時封鎖 Windows Communication Foundation WMI 提供者的安裝。 在安裝期間，Windows Communication Foundation 安裝程式無法使用*mofcomp.exe*元件註冊 WCF *. mof*檔案。 可能徵兆如下所示：  
  
1. .NET Framework 3.0 安裝成功完成，不過 WCF WMI 提供者並未註冊。  
  
2. 應用程式記錄檔中顯示關於在註冊 WCF 的 WMI 提供者、或執行 mofcomp.exe 時所發生問題的錯誤事件。  
  
3. 在使用者的 %temp% 目錄中名為 dd_wcf_retCA* 的安裝記錄檔，包含了無法註冊 WCF WMI 提供者的相關資訊。  
  
4. 在事件記錄檔或安裝追蹤記錄檔中，可能會列出下列其中一個例外狀況 (Exception)：  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: 以 "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" 執行 E:\WINDOWS\system32\wbem\mofcomp.exe 時產生未預期的結果 3  
  
     或者：  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: 'System.Management.ManagementPath' 的型別初始設定式發生例外狀況。 ---> System.runtime.interopservices.outattribute. COMException (0x80040154) ：為 CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} 的元件抓取 COM class factory 失敗，因為發生下列錯誤：80040154。  
  
     或者：  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: 無法載入檔案或組件 'C:\WINDOWS\system32\wbem\mofcomp.exe' 或其相依性的其中之一。 系統找不到指定的檔案。  
  
     檔案名稱：'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 您必須遵循下列步驟才能解決上述問題。  
  
1. 執行 WMI Diagnosis Utility 以修復 WMI 服務。 如需使用此工具的詳細資訊，請參閱 [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10))。  
  
 使用位於**主控台**中的 [**新增/移除程式**] 小程式，或卸載/重新安裝 .NET Framework 3.0，以修復 .NET Framework 3.0 安裝。  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a>在 .NET Framework 3.5 安裝之後修復 .NET Framework 3。0

 如果您在安裝 .NET Framework 3.5 之後修復 .NET Framework 3.0，則會移除 *machine.config* 中 .NET Framework 3.5 所引進的設定元素。 不過， *web.config* 檔案會保持不變。 因應措施是透過 ARP 來修復 .NET Framework 3.5，或使用 [工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) 搭配 `/c` 參數。  
  
 您可以在%windir%\Microsoft.NET\framework\v3.5\ 或%windir%\Microsoft.NET\framework64\v3.5\ 找到[工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md)  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>在安裝 .NET Framework 3.5 之後，適當地為 WCF/WF Webhost 設定 IIS  
 當 .NET Framework 3.5 安裝無法設定其他與 WCF 相關的 IIS 設定時，它會在安裝記錄檔中記錄錯誤，並繼續進行。 任何執行 WorkflowServices 應用程式的嘗試都將失敗，因為缺少必要的組態設定。 例如，無法載入 xoml 或規則服務。  
  
 若要解決這個問題，請使用 [工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) 搭配 `/c` 參數，以在電腦上正確設定 IIS 腳本對應。 您可以在%windir%\Microsoft.NET\framework\v3.5\ 或%windir%\Microsoft.NET\framework64\v3.5\ 找到[工作流程服務註冊工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md)  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a>無法載入類型 ' HttpModule '

**無法從元件 ' System.servicemodel，Version 3.0.0.0，Culture = 中性，PublicKeyToken = b77a5c561934e089 ' 載入類型 ' HttpModule '**

 如果已安裝 .NET Framework 4，然後啟用 WCF HTTP 啟用，就會發生此錯誤。 若要解決此問題，請從開發人員命令提示字元內部執行下列命令，以進行 Visual Studio：  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>另請參閱

- [設定指示](./samples/set-up-instructions.md)
