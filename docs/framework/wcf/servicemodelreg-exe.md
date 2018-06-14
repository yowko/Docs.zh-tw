---
title: ServiceModel 註冊工具 (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808922"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel 註冊工具 (ServiceModelReg.exe)
這個命令列工具可讓您在單一電腦上管理 WCF 及 WF 元件的註冊。 在一般情況下，您應該不需要使用這個工具，因為安裝時已對 WCF 及 WF 元件進行設定。 但如果您遇到服務啟用的問題，您可以嘗試使用這個工具來註冊元件。  
  
## <a name="syntax"></a>語法  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>備註  
 您可以在下列位置找到這個工具：  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
>  ServiceModel 註冊工具上執行時[!INCLUDE[wv](../../../includes/wv-md.md)]、 **Windows 功能**對話方塊可能不會反映**Windows Communication Foundation HTTP 啟動**下的選項**Microsoft.NET Framework 3.0**已開啟。 **Windows 功能**對話方塊可以透過按一下**啟動**，然後按一下 **執行**然後輸入**OptionalFeatures**。  
  
 下表說明可與 ServiceModelReg.exe 搭配使用的選項。  
  
|選項|描述|  
|------------|-----------------|  
|`-ia`|安裝所有 WCF 和 WF 元件。|  
|`-ua`|解除安裝所有 WCF 和 WF 元件。|  
|`-r`|修復所有 WCF 和 WF 元件。|  
|`-i`|安裝使用 –c 所指定的 WCF 和 WF 元件。|  
|`-u`|解除安裝使用 –c 所指定的 WCF 和 WF 元件。|  
|`-c`|安裝或解除安裝元件：<br /><br /> -httpnamespace-HTTP 命名空間保留<br />-tcpportsharing-TCP 連接埠共用服務<br />-tcpactivation – TCP 啟用服務 （不支援在.NET 4 用戶端設定檔）<br />-namedpipeactivation – 具名管道啟用服務 （不支援在.NET 4 用戶端設定檔<br />-msmqactivation – MSMQ 啟用服務 （不支援在.NET 4 用戶端設定檔<br />-etw-ETW 事件追蹤資訊清單 (Windows Vista 或更新版本)|  
|`-q`|無訊息模式 (僅顯示錯誤記錄)|  
|`-v`|詳細資訊模式。|  
|`-nologo`|不顯示版權和橫幅訊息。|  
|`-?`|顯示說明文字|  
  
## <a name="fixing-the-fileloadexception-error"></a>修正 FileLoadException 錯誤  
 如果您在電腦上安裝 WCF 的舊版，您可能會得到`FileLoadFoundException`當您執行 ServiceModelReg 工具註冊新安裝的錯誤。 即使您已手動移除舊安裝中的檔案，但 machine.config 設定仍保留原封不動，仍將發生這種情形。  
  
 得到的錯誤訊息與以下類似。  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 您會在錯誤訊息中發現，先前發行的 Customer Technology Preview (CTP) 安裝了 System.ServiceModel Version 2.0.0.0 組件。 System.ServiceModel 組件目前的版本是 3.0.0.0。 因此，當您想要其中 WCF 早期的 CTP 版本已安裝，但不是完全解除安裝的機器上安裝官方 WCF 版本時，會發生這個問題。  
  
 ServiceModelReg.exe 無法清除舊版的項目，也無法註冊新版本項目。 唯一的解決方法就是手動編輯 machine.config。您可以在下列位置找到這個檔案。  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 如果您執行 WCF 64 位元電腦上，您也應該編輯此位置的相同檔案。  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 參考這個檔案中找到的任何 XML 節點"System.ServiceModel，Version = 2.0.0.0"，刪除這些節點及其任何子節點。 儲存檔案並重新執行 ServiceModelReg.exe，便可解決這個問題。  
  
## <a name="examples"></a>範例  
 下列範例顯示如何使用 ServiceModelReg.exe 工具的最常見選項。  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
