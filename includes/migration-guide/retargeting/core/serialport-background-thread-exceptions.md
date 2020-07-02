---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614360"
---
### <a name="serialport-background-thread-exceptions"></a>SerialPort 背景執行緒例外狀況

#### <a name="details"></a>詳細資料

使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒與不會再於擲回 OS 的例外狀況時終止處理序。 <br/>在以 .NET Framework 4.7 和舊版為目標的應用程式中，當使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒上擲回作業系統例外狀況時，處理程序會終止。 <br/>在目標為 .NET Framework 4.7.1 或更新版本的應用程式中，背景執行緒會等候與作用中的序列連接埠相關且在某些情況下可能會損毀的 OS 事件，例如突然移除序列連接埠。

#### <a name="suggestion"></a>建議

若為以 .NET Framework 4.7.1 為目標的應用程式，如果不需要例外狀況處理，您可以透過將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段以選擇退出例外狀況處理︰

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.7.1 或更新版本上執行的應用程式，則可將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，以選擇加入例外狀況處理：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
