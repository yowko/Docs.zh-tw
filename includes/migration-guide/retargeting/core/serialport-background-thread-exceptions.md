---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614360"
---
### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="51b2b-101">SerialPort 背景執行緒例外狀況</span><span class="sxs-lookup"><span data-stu-id="51b2b-101">SerialPort background thread exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="51b2b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="51b2b-102">Details</span></span>

<span data-ttu-id="51b2b-103">使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒與不會再於擲回 OS 的例外狀況時終止處理序。</span><span class="sxs-lookup"><span data-stu-id="51b2b-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="51b2b-104">在以 .NET Framework 4.7 和舊版為目標的應用程式中，當使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒上擲回作業系統例外狀況時，處理程序會終止。</span><span class="sxs-lookup"><span data-stu-id="51b2b-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="51b2b-105">在目標為 .NET Framework 4.7.1 或更新版本的應用程式中，背景執行緒會等候與作用中的序列連接埠相關且在某些情況下可能會損毀的 OS 事件，例如突然移除序列連接埠。</span><span class="sxs-lookup"><span data-stu-id="51b2b-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="51b2b-106">建議</span><span class="sxs-lookup"><span data-stu-id="51b2b-106">Suggestion</span></span>

<span data-ttu-id="51b2b-107">若為以 .NET Framework 4.7.1 為目標的應用程式，如果不需要例外狀況處理，您可以透過將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段以選擇退出例外狀況處理︰</span><span class="sxs-lookup"><span data-stu-id="51b2b-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

<span data-ttu-id="51b2b-108">若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.7.1 或更新版本上執行的應用程式，則可將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，以選擇加入例外狀況處理：</span><span class="sxs-lookup"><span data-stu-id="51b2b-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| <span data-ttu-id="51b2b-109">名稱</span><span class="sxs-lookup"><span data-stu-id="51b2b-109">Name</span></span>    | <span data-ttu-id="51b2b-110">值</span><span class="sxs-lookup"><span data-stu-id="51b2b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="51b2b-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="51b2b-111">Scope</span></span>   | <span data-ttu-id="51b2b-112">Minor</span><span class="sxs-lookup"><span data-stu-id="51b2b-112">Minor</span></span>       |
| <span data-ttu-id="51b2b-113">版本</span><span class="sxs-lookup"><span data-stu-id="51b2b-113">Version</span></span> | <span data-ttu-id="51b2b-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="51b2b-114">4.7.1</span></span>       |
| <span data-ttu-id="51b2b-115">類型</span><span class="sxs-lookup"><span data-stu-id="51b2b-115">Type</span></span>    | <span data-ttu-id="51b2b-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="51b2b-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="51b2b-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="51b2b-117">Affected APIs</span></span>

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
