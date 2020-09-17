---
title: WS-AtomicTransaction 組態公用程式 (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: dbd33869de6b1ecee6406dfeede88afc4eca07f1
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720487"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction 組態公用程式 (wsatConfig.exe)

WS-AtomicTransaction 組態公用程式用於設定基本的 WS-AtomicTransaction 支援設定。  
  
## <a name="syntax"></a>語法  
  
```console  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>備註

 此命令列工具只能用來設定本機電腦中的基本 WS-AT 設定。 如果您必須在本機和遠端電腦上進行設定，則應使用 MMC 嵌入式管理單元，如設定 WS-不可部分完成的 [交易支援](./feature-details/configuring-ws-atomic-transaction-support.md)中所述。  
  
 您可以在 Windows SDK 安裝位置找到命令列工具：
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe
  
 下表顯示與 WS-AtomicTransaction 組態公用程式 (wsatConfig.exe) 搭配使用的選項。  
  
> [!NOTE]
> 為選取的連接埠設定 SSL 憑證時，如果與該連接埠關聯的原始 SSL 憑證存在的話，將會覆寫該憑證。  
  
|選項。|描述|  
|-------------|-----------------|  
|帳目\<account,>|指定可以參與 WS-AtomicTransaction 的帳戶逗號分隔清單。 這些帳戶的有效性並未經過檢查。|  
|-accountsCerts： \<thumb>&#124; "Issuer\SubjectName"，>|指定可以參與 WS-AtomicTransaction 的憑證逗號分隔清單。 憑證由指紋或 Issuer\SubjectName 配對所指定。 如果主體名稱為空白，請使用 {EMPTY} 做為主體名稱。|  
|-endpointCert： <電腦&#124;\<thumb>&#124; "Issuer\SubjectName" >|使用電腦憑證或其他由指紋或 Issuer\SubjectName 配對指定的本機端點憑證。 如果主體名稱為空白，請使用 {EMPTY} 做為主體名稱。|  
|maxTimeout\<sec>|以秒數為單位指定最大逾時值。 有效的值是從0到3600。|  
|網路\<enable&#124;disable>|啟用或停用 WS-AtomicTransaction 網路支援。|  
|埠\<portNum>|設定 WS-AtomicTransaction 的 HTTPS 連接埠。<br /><br /> 如果在執行此工具之前，您已啟用防火牆，則會自動在例外狀況清單中註冊該連接埠。 如果在執行此工具之前，您已停用防火牆，則不必為該防火牆進行任何額外的設定。<br /><br /> 如果您在設定 WS-AT 後，啟用了防火牆，您必須再次執行這個工具，並使用這個參數提供連接埠號碼。 如果您在設定後停用防火牆，WS-AT 會繼續運作，而不必進行額外的輸入。|  
|中超\<sec>|以秒數為單位指定預設逾時值。 有效值為 1 到 3600。|  
|traceActivity\<enable&#124;disable>|啟用或停用活動事件追蹤。|  
|-traceLevel： \<Off&#124;Error&#124;Critical&#124;Warning&#124;Information&#124; Verbose&#124;All> }|指定追蹤層級。|  
|-tracePII:\<enable&#124;disable>|啟用或停用個人可識別資訊追蹤。|  
|-traceProp:\<enable&#124;disable>|啟用或停用傳播事件追蹤。|  
|-restart|重新啟動 MSDTC 以立即啟動變更。 如果未指定，則變更會在 MSDTC 重新啟動時生效。|  
|-show|顯示目前的 WS-AtomicTransaction 通訊協定設定。|  
|virtualServer\<virtualServer>|指定 DTC 資源叢集名稱。|  
  
## <a name="see-also"></a>另請參閱

- [使用 WS-AtomicTransaction](./feature-details/using-ws-atomictransaction.md)
- [設定 WS-Atomic 交易支援](./feature-details/configuring-ws-atomic-transaction-support.md)
