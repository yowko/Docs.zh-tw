---
title: 在 .NET 中處理 I/O 錯誤
ms.date: 08/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d2ff4e69596e721f485d107317f261231615c5a6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126871"
---
# <a name="handling-io-errors-in-net"></a>在 .NET 中處理 I/O 錯誤

除了在任何方法呼叫中擲回的例外狀況以外 (例如系統負荷過高造成的 <xref:System.OutOfMemoryException>，或程式設計人員出錯造成的 <xref:System.NullReferenceException>)，.NET 檔案系統方法還會擲回下列例外狀況：

- <xref:System.IO.IOException?displayProperty=nameWithType>，所有 <xref:System.IO> 例外狀況類型的基底類別。 之所以會擲回此例外狀況，是因為來自作業系統的錯誤傳回碼沒有直接對應到任何其他例外狀況類型。
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>，針對 .NET Framework 和 .NET Core 2.0 及更早版本上的無效路徑字元擲回。
- <xref:System.NotSupportedException?displayProperty=nameWithType>，針對 .NET Framework 中的無效冒號擲回。
- <xref:System.Security.SecurityException?displayProperty=nameWithType>，此例外狀況是因為應用程式在有限信任中執行而擲回，其缺少僅在 .NET Framework 上適用的必要權限。 (.NET Framework 上預設是完全信任。)

## <a name="mapping-error-codes-to-exceptions"></a>將錯誤碼對應至例外狀況

因為檔案系統是作業系統資源，所以 .NET Core 和 .NET Framework 兩者中的 I/O 方法會將呼叫包裝至基礎作業系統。 在作業系統所執行的程式碼中發生 I/O 錯誤時，作業系統會將錯誤資訊傳回給 .NET I/O 方法。 接著方法會將錯誤資訊 (通常是錯誤碼的形式) 轉譯為 .NET 例外狀況類型。 在大部分情況下，這個作業是藉由直接將錯誤碼轉譯為其對應例外狀況類型來完成；不會根據方法呼叫的內容來執行任何特殊的錯誤對應。

例如在 Windows 作業系統上，傳回 `ERROR_FILE_NOT_FOUND` 錯誤碼 (或 0x02) 的方法呼叫會對應至 <xref:System.IO.FileNotFoundException>，傳回 `ERROR_PATH_NOT_FOUND` 錯誤碼 (或 0x03) 的方法呼叫會對應至 <xref:System.IO.DirectoryNotFoundException>。

不過，作業系統會傳回特定錯誤碼的精確條件，通常未記載或記載不佳。 因此會發生未預期的例外狀況。 例如，因為您使用目錄而不是檔案，您可預期對 <xref:System.IO.DirectoryInfo.%23ctor%2A?displayProperty=nameWithType> 建構函式提供無效的目錄路徑會擲回 <xref:System.IO.DirectoryNotFoundException>。 不過，它也可能會擲回 <xref:System.IO.FileNotFoundException>。

## <a name="exception-handling-in-io-operations"></a>I/O 作業中的例外狀況處理

因為必須依賴作業系統，所以相同的例外狀況 (例如我們範例中的找不到目錄錯誤) 會導致 I/O 方法擲回 I/O 例外狀況的任何一個完整類別。 這表示在呼叫 I/O API 時，您的程式碼應該已準備好處理大部分或所有例外狀況，如下表所示：

| 例外狀況類型 | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | 是 | [是] |
| <xref:System.IO.FileNotFoundException> | 是 | 是 |
| <xref:System.IO.DirectoryNotFoundException> | 是 | 是 |
| <xref:System.IO.DriveNotFoundException?> | [是] | 是 |
| <xref:System.IO.PathTooLongException> | 是 | [是] |
| <xref:System.OperationCanceledException> | [是] | 是 |
| <xref:System.UnauthorizedAccessException> | [是] | [是] |
| <xref:System.ArgumentException> | .NET Core 2.0 及更早版本| 是 |
| <xref:System.NotSupportedException> | 否 | [是] |
| <xref:System.Security.SecurityException> | 否 | 僅限有限信任 |

## <a name="handling-ioexception"></a>處理 IOException

作為 <xref:System.IO> 命名空間中例外狀況的基底類別，<xref:System.IO.IOException> 也會因為任何錯誤碼未對應至預先定義的例外狀況類型而擲回。 這表示此例外狀況可由任何 I/O 作業擲回。

> [!IMPORTANT]
> 因為 <xref:System.IO.IOException> 是 <xref:System.IO> 命名空間中其他例外狀況類型的基底類別，所以您應該在處理過其他 I/O 相關例外狀況之後，在 `catch` 區塊中處理此例外狀況。

此外，從 .NET Core 2.1 開始，已移除路徑正確性的驗證檢查 (例如，為了確保無效字元不會出現在路徑中)，而且執行階段會從作業系統錯誤碼而非它自己的驗證碼，擲回對應的例外狀況。 在此情況下最有可能擲回的例外狀況是 <xref:System.IO.IOException>，但是也可能會擲回其他任何例外狀況類型。

請注意，在您的例外狀況處理程式碼中，您應該一律最後處理 <xref:System.IO.IOException>。 否則，因為它是其他所有 IO 例外狀況的基底類別，會造成衍生類別的 Catch 區塊不會受到評估。

若是 <xref:System.IO.IOException>，您可以從 [IOException.HResult](xref:System.Exception.HResult) 屬性取得額外的錯誤資訊。 若要將 HResult 值轉換為 Win32 錯誤碼，您要去除 32 位元值的前 16 位元。 下表列出可能包裝在 <xref:System.IO.IOException> 中的錯誤碼。

| HResult | 常數 | 說明 |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | 遺漏檔案名稱，或者檔案或目錄正在使用中。 |
| ERROR_FILE_EXISTS | 80 | 檔案已存在。 |
| ERROR_INVALID_PARAMETER | 87 | 提供給方法的引數無效。 |
| ERROR_ALREADY_EXISTS | 183 | 檔案或目錄已存在。 |

您可以在 Catch 陳述式中使用 `When` 子句來進行處理，如下列範例所示。

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>另請參閱

- [在 .NET 中處理和擲回例外狀況](../exceptions/index.md)
- [例外狀況處理 (工作平行程式庫)](../parallel-programming/exception-handling-task-parallel-library.md)
- [例外狀況的最佳做法](../exceptions/best-practices-for-exceptions.md)
- [如何使用 Catch 區塊中的特定例外狀況](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
