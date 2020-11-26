---
title: 傾印-.NET
description: .NET 中傾印的簡介。
ms.date: 10/12/2020
ms.openlocfilehash: 56cf4085d10658c828bac39be93eed3f774e00d5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242769"
---
# <a name="dumps"></a>傾印

傾印是一個檔案，其中包含建立進程的快照集，而且在檢查應用程式的狀態時很有用。 當您很難將偵錯工具附加至應用程式，例如生產或 CI 環境時，可使用傾印來對 .NET 應用程式進行偵錯工具。 使用傾印可讓您捕捉有問題的程式狀態，並檢查它，而不需要停止應用程式。

## <a name="collect-dumps"></a>收集傾印

您可以透過各種方式收集傾印，視您執行應用程式的平臺而定。

> [!NOTE]
> 在容器內收集傾印需要 PTRACE 功能，可透過 `--cap-add=SYS_PTRACE` 或新增 `--privileged` 。

> [!NOTE]
> 傾印可能包含機密資訊，因為它們可以包含執行中進程的完整記憶體。 請注意任何安全性限制和 guidances 的處理方式。

### <a name="collecting-dumps-on-crash"></a>在損毀時收集傾印

您可以使用環境變數來設定應用程式，以在損毀時收集傾印。 當您想要瞭解發生損毀的原因時，這會很有説明。 例如，當擲回例外狀況時，捕捉傾印可協助您在應用程式損毀時檢查應用程式的狀態，以找出問題。

下表顯示您可以設定的環境變數，以便在損毀時收集傾印。

|環境變數|描述|預設值|
|-------|---------|---|
|`COMPlus_DbgEnableMiniDump`|如果設定為1，則啟用核心傾印產生。|0|
|`COMPlus_DbgMiniDumpType`|要收集的傾印類型。 如需詳細資訊，請參閱下表|2 (`MiniDumpWithPrivateReadWriteMemory`) |
|`COMPlus_DbgMiniDumpName`|寫入傾印之檔案的路徑。|`/tmp/coredump.<pid>`|
|`COMPlus_CreateDumpDiagnostics`|如果設定為1，則啟用傾印處理的診斷記錄。|0|

下表顯示您可以用來指定做為值的所有選項 `COMPlus_DbgMiniDumpType` 。 例如，將設定 `COMPlus_DbgMiniDumpType` 為1，表示 `MiniDumpNormal` 會在損毀時收集型別傾印。

|值|名稱|描述|
|-----|----|-----------|
|1|`MiniDumpNormal`|只包含為進程中所有現有線程捕捉堆疊追蹤所需的資訊。 有限的 GC 堆積記憶體和資訊。|
|2|`MiniDumpWithPrivateReadWriteMemory`|包含 GC 堆積以及在進程中為所有現有線程捕捉堆疊追蹤所需的資訊。|
|3|`MiniDumpFilterTriage`|只包含為進程中所有現有線程捕捉堆疊追蹤所需的資訊。 有限的 GC 堆積記憶體和資訊。|
|4|`MiniDumpWithFullMemory`|在進程中包含所有可存取的記憶體。 原始記憶體資料會包含在結尾，因此可以直接對應初始結構，而不需要原始記憶體資訊。 此選項可能會產生非常大的檔案。|

### <a name="collecting-dumps-at-specific-point-in-time"></a>在特定時間點收集傾印

當應用程式尚未損毀時，您可能會想要收集傾印。 例如，如果您想要檢查看似處於鎖死的應用程式狀態，則設定環境變數以收集損毀傾印時，將不會有説明，因為應用程式仍在執行中。

若要在您自己的要求中收集傾印，您可以使用 `dotnet-dump` ，這是用來收集和分析傾印的 CLI 工具。 如需如何使用它來收集傾印的詳細資訊 `dotnet-dump` ，請參閱傾印 [收集和分析公用程式](dotnet-dump.md)。

## <a name="analyze-dumps"></a>分析傾印

傾印可使用進行分析 [`dotnet-dump`](dotnet-dump.md) 。

## <a name="see-also"></a>另請參閱

深入瞭解您可以如何運用傾印來協助診斷 .NET 應用程式中的問題。

* [Debug linux](debug-linux-dumps.md) 傾印教學課程會逐步解說如何對在 Linux 中收集的傾印進行 debug 錯。

* [Debug 鎖死](debug-deadlock.md) 教學課程會逐步引導您使用傾印，在 .net 應用程式中進行鎖死的偵測。
