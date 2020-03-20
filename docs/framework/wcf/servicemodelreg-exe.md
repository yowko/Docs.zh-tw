---
title: ServiceModel 註冊工具 (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183099"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel 註冊工具 (ServiceModelReg.exe)
這個命令列工具可讓您在單一電腦上管理 WCF 及 WF 元件的註冊。 在一般情況下，您應該不需要使用這個工具，因為安裝時已對 WCF 及 WF 元件進行設定。 但如果您遇到服務啟用的問題，您可以嘗試使用這個工具來註冊元件。  
  
## <a name="syntax"></a>語法  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>備註  
 您可以在下列位置找到這個工具：  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> 在 Windows Vista 上運行服務模式註冊工具時 **，"Windows 功能"** 對話方塊可能不會反映**Microsoft .NET 框架 3.0**下的**Windows 通信基礎 HTTP 啟動**選項已打開。 可通過按一下 **"開始"（"開始"）** 然後按一下"**運行**"然後鍵入可選功能來訪問**Windows** **功能對話方塊**。  
  
 下表說明可與 ServiceModelReg.exe 搭配使用的選項。  
  
|選項|描述|  
|------------|-----------------|  
|`-ia`|安裝所有 WCF 和 WF 元件。|  
|`-ua`|解除安裝所有 WCF 和 WF 元件。|  
|`-r`|修復所有 WCF 和 WF 元件。|  
|`-i`|安裝使用 –c 所指定的 WCF 和 WF 元件。|  
|`-u`|解除安裝使用 –c 所指定的 WCF 和 WF 元件。|  
|`-c`|安裝或解除安裝元件：<br /><br /> - HTTP 命名空間 + HTTP 命名空間保留<br />- tcp埠共用 + TCP 埠共用服務<br />- tcp啟動 = TCP 啟動服務（.NET 4 用戶端設定檔上不受支援）<br />- 具名管道啟動 • 具名管道啟動服務（.NET 4 用戶端設定檔上不受支援）<br />- msmq啟動 = MSMQ 啟動服務（.NET 4 用戶端設定檔上不受支援）<br />- etw = ETW 事件跟蹤清單（視窗 Vista 或更高版本）|  
|`-q`|無訊息模式 (僅顯示錯誤記錄)|  
|`-v`|詳細資訊模式。|  
|`-nologo`|不顯示版權和橫幅訊息。|  
|`-?`|顯示說明文字|  
  
## <a name="fixing-the-fileloadexception-error"></a>修正 FileLoadException 錯誤  
 如果在電腦上安裝了以前版本的 WCF，則在運行 ServiceModelReg`FileLoadFoundException`工具以註冊新安裝時可能會收到錯誤。 即使您已手動移除舊安裝中的檔案，但 machine.config 設定仍保留原封不動，仍將發生這種情形。  
  
 得到的錯誤訊息與以下類似。  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 您會在錯誤訊息中發現，先前發行的 Customer Technology Preview (CTP) 安裝了 System.ServiceModel Version 2.0.0.0 組件。 System.ServiceModel 組件目前的版本是 3.0.0.0。 因此，當您要在安裝了 WCF 的早期 CTP 版本但未完全卸載的電腦上安裝正式 WCF 版本時，會遇到此問題。  
  
 ServiceModelReg.exe 無法清除舊版的項目，也無法註冊新版本項目。 唯一的解決方法就是手動編輯 machine.config。您可以在下列位置找到這個檔案。  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 如果在 64 位電腦上運行 WCF，則還應在此位置編輯同一檔。  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 在此檔中查找引用"System.ServiceModel、版本=2.0.0.0"的任何 XML 節點，刪除它們和任何子節點。 儲存檔案並重新執行 ServiceModelReg.exe，便可解決這個問題。  
  
## <a name="examples"></a>範例  
 下列範例顯示如何使用 ServiceModelReg.exe 工具的最常見選項。  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
