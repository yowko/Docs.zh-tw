---
title: 疑難排解安裝程式問題
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 326daab1f7df5f8a4ea4f74fd8890031f243f7f5
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291521"
---
# <a name="troubleshooting-setup-issues"></a>疑難排解安裝程式問題
本主題描述如何針對 Windows Communication Foundation （WCF）設定問題進行疑難排解。  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>有些 Windows Communication Foundation 登錄機碼 (Registry Key) 無法藉由在 .NET Framework 3.0 上執行 MSI 修復作業來加以修復。  
 如果您刪除下列任何登錄機碼：  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 如果您使用從 [**控制台**] 中的 [**新增/移除程式**] applet 啟動的 .NET Framework 3.0 安裝程式執行修復，則不會重新建立金鑰。 若要正確地重新建立這些機碼，使用者必須解除安裝並重新安裝 .NET Framework 3.0。  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>WMI 服務損毀在 .NET Framework 3.0 套件安裝期間封鎖 Windows Communication Foundation WMI 提供者的安裝  
 WMI 服務損毀可能會封鎖 Windows Communication Foundation WMI 提供者的安裝。 在進行安裝時，Windows Communication Foundation 安裝程式無法使用 mofcomp.exe 元件來註冊 WCF .mof 檔。 可能徵兆如下所示：  
  
1. .NET Framework 3.0 安裝成功完成，不過 WCF WMI 提供者並未註冊。  
  
2. 應用程式記錄檔中顯示關於在註冊 WCF 的 WMI 提供者、或執行 mofcomp.exe 時所發生問題的錯誤事件。  
  
3. 在使用者的 %temp% 目錄中名為 dd_wcf_retCA* 的安裝記錄檔，包含了無法註冊 WCF WMI 提供者的相關資訊。  
  
4. 在事件記錄檔或安裝追蹤記錄檔中，可能會列出下列其中一個例外狀況 (Exception)：  
  
     Servicemodelreg.exe [11:09:59:046]：System.ApplicationException:非預期的結果3執行具有 "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" 的 E:\WINDOWS\system32\wbem\mofcomp.exe  
  
     或：  
  
     Servicemodelreg.exe [07:19:33:843]：System.typeinitializationexception：' ManagementPath ' 的類型初始化運算式擲回例外狀況。 ---> System.runtime.interopservices.outattribute. COMException （0x80040154）：因為發生下列錯誤，所以無法為 CLSID 為 {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} 的元件抓取 COM Class Factory：80040154。  
  
     或：  
  
     Servicemodelreg.exe [07:19:32:750]：System.IO.FileNotFoundException:無法載入檔案或元件 ' C:\WINDOWS\system32\wbem\mofcomp.exe ' 或它的其中一個相依性。 系統找不到指定的檔案。  
  
     檔案名稱：'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 您必須遵循下列步驟才能解決上述問題。  
  
1. 執行[2.0 版的 WMI Diagnosis Utility，](https://go.microsoft.com/fwlink/?LinkId=94685)以修復 WMI 服務。 如需使用此工具的詳細資訊，請參閱[WMI Diagnosis Utility](https://go.microsoft.com/fwlink/?LinkId=94686)主題。  
  
 使用位於 [**控制台**] 中的 [**新增/移除程式**] applet，或卸載/重新安裝 .NET Framework 3.0，以修復 .NET Framework 3.0 安裝。  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>在安裝 .NET Framework 3.5 後修復 .NET Framework 3.0 會將 machine.config 中由 .NET Framework 3.5 引入的組態項目移除  
 如果您要在安裝 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 後修復 .NET Framework 3.0，則會將 machine.config 中由 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 引入的組態項目移除。 不過，web.config 會保持不變。 因應措施是透過 ARP 在此之後修復 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]，或使用[工作流程服務註冊工具（wfservicesreg.exe）](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)搭配 `/c` 參數。  
  
 您可以在%windir%\Microsoft.NET\framework\v3.5\ 或%windir%\Microsoft.NET\framework64\v3.5\ 找到[工作流程服務註冊工具（wfservicesreg.exe .exe）](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>在安裝 .NET Framework 3.5 之後，適當地為 WCF/WF Webhost 設定 IIS  
 當 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 安裝無法設定其他與 WCF 相關的 IIS 設定時，會在安裝記錄檔中記錄錯誤並繼續進行。 任何執行 WorkflowServices 應用程式的嘗試都將失敗，因為缺少必要的組態設定。 例如，無法載入 xoml 或規則服務。  
  
 若要解決這個問題，請使用[工作流程服務註冊工具（wfservicesreg.exe）](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)搭配 `/c` 參數，在電腦上正確設定 IIS 腳本對應。 您可以在%windir%\Microsoft.NET\framework\v3.5\ 或%windir%\Microsoft.NET\framework64\v3.5\ 找到[工作流程服務註冊工具（wfservicesreg.exe .exe）](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md)  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>無法從組件 ‘System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089’ 載入類型 ‘System.ServiceModel.Activation.HttpModule’  
 如果已安裝 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]，而且已啟用 WCF HTTP 啟用，就會發生此錯誤。 若要解決此問題，請從開發人員命令提示字元的 Visual Studio 中執行下列命令列：  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>另請參閱

- [設定指示](../../../docs/framework/wcf/samples/set-up-instructions.md)
