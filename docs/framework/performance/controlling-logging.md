---
title: 控制 .NET Framework 記錄
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6f6744451bf3436e58a3ff9efcdb16ceee08c9d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489751"
---
# <a name="controlling-net-framework-logging"></a>控制 .NET Framework 記錄
您可以使用 Windows 事件追蹤 (ETW) 來記錄通用語言執行平台 (CLR) 事件。 您可以使用下列工具來建立和檢視追蹤：  
  
- [Logman](/windows-server/administration/windows-commands/logman) 和 [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) 命令列工具，隨附於 Windows 作業系統。  
  
- [Windows 效能工具組](/windows-hardware/test/wpt/)中的 [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) 工具。 如需 Xperf 的詳細資訊，請參閱 [Windows 效能部落格](https://go.microsoft.com/fwlink/?LinkId=179509)。  
  
 若要擷取 CLR 事件資訊，您必須在電腦上安裝 CLR 提供者。 若要確認是否已安裝此提供者，請在命令提示字元中輸入 `logman query providers`。 提供者的清單隨即顯示。 此清單應該會包含 CLR 提供者的項目，如下所示。  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 如果未列出 CLR 提供者，您可以使用 Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) 命令列工具，在 Windows Vista 和更新版本的作業系統上安裝此提供者。 以系統管理員身分開啟 [命令提示字元] 視窗。 將提示目錄變更為 [.NET Framework 4] 資料夾 (%windir%\microsoft.net\framework[64]\v4。\<.NET 版本 > \)。 這個資料夾包含 CLR-ETW.man 檔案。 在命令提示字元中，輸入下列命令，即可安裝 CLR 提供者：  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a>擷取 CLR ETW 事件  
 您可以使用 [Logman](/windows-server/administration/windows-commands/logman) 和 [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) 命令列工具擷取 ETW 事件，以及使用 [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) 和 [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) 工具解碼追蹤事件。  
  
 若要開啟記錄，使用者必須指定三個項目：  
  
- 要與之通訊的提供者。  
  
- 表示一組關鍵字的 64 位元數字。 每個關鍵字各表示一組提供者可以開啟的事件。 數字綜合表示一組要開啟的關鍵字。  
  
- 很小的數字，表示要記錄的 (詳細) 層級。 層級 1 最不詳細，而層級 5 則是最詳細。 層級 0 為預設值，意思是提供者特有的事件。  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a>若要使用 Logman 來擷取 CLR ETW 事件  
  
1. 在命令提示中，輸入：  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     其中：  
  
    - `-p` 參數會識別提供者 GUID。  
  
    - `0x1CCBD` 會指定即將引發之事件的分類。  
  
    - `0x5` 會設定記錄的層級 (在本例中，設為詳細資訊 (5))。  
  
    - `-ets` 參數會指示 Logman 傳送命令給事件追蹤工作階段。  
  
    - `-ct perf` 參數會指定要使用 `QueryPerformanceCounter` 函式來記錄每個事件的時間戳記。  
  
2. 若要停止記錄事件，請輸入：  
  
     `logman stop clrevents -ets`  
  
     這個命令會建立名為 clrevents.etl 的二進位追蹤檔。  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a>若要使用 Xperf 來擷取 CLR ETW 事件  
  
1. 在命令提示中，輸入：  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     其中，GUID 是 CLR ETW 提供者 GUID，而且 `0x1CCBD:5` 會追蹤層級 5 (詳細資訊) 以下的每個事件。  
  
2. 若要停止追蹤，請輸入：  
  
     `Xperf -stop clr`  
  
     這個命令會建立名為 clrevents.etl 的追蹤檔。  
  
## <a name="viewing-clr-etw-events"></a>檢視 CLR ETW 事件  
 您可以使用下列命令來檢視 CLR ETW 事件。 如需這些事件的描述，請參閱 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)。  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a>若要使用 Tracerpt 來檢視 CLR ETW 事件  
  
- 在命令提示中，輸入：  
  
     `tracerpt clrevents.etl`  
  
     這個命令會建立兩個檔案：dumpfile.xml 和 summary.txt。 dumpfile.xml 檔案會列出所有事件，而 summary.txt 會提供這些事件的摘要。  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a>若要使用 Xperf 來檢視 CLR ETW 事件  
  
- 在命令提示中，輸入：  
  
     `xperf clrevents.etl`  
  
     這個命令會開啟 Xperf ETL 檔案檢視器。 在這個檢視器中，CLR 事件會顯示在 [一般事件]  檢視中。 若要顯示依類型分類的事件資料格，請在這個檢視中選取一個時間區域，並按一下滑鼠右鍵，然後選取 [摘要]  。  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>若要將 .etl 檔案轉換為逗點分隔值檔案  
  
- 在命令提示中，輸入：  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     這個命令會讓 XPerf 以您可以檢視的逗點分隔值 (CSV) 檔案的形式傾印事件。 因為不同的事件有不同的欄位，所以這個 CSV 檔案中的資料前面會有多行標頭。 每行的第一個欄位都是事件類型，表示應使用哪一行的標頭來判斷其餘的欄位。  
  
## <a name="see-also"></a>另請參閱

- [Windows 效能工具組](/windows-hardware/test/wpt/)
- [Common Language Runtime 中的 ETW 事件](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
