---
title: 讓映射在 .NET 中更容易進行偵錯工具
description: 瞭解如何使用 IDE 參數和命令列選項，設定可執行映射以更輕鬆地進行偵錯工具。
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b64bd1e112932f394bb473a21642d37e28e39d3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052507"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>讓映射在 .NET 中更容易進行偵錯工具

當編譯 Unmanaged 程式碼時，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。 例如，您可以在 Visual C++ 中使用 /**Zi** 命令列選項，要求它發出偵錯符號檔 (副檔名為 .pdb)。 同樣地，/**Od** 命令列選項會通知編譯器停用最佳化。 產生的程式碼執行速度較慢，但這是必要的更容易的偵錯工具。

在編譯 .NET Framework managed 程式碼時，編譯器（ C++例如視覺效果） C# Visual Basic，並將其原始程式編譯成 MICROSOFT 中繼語言（MSIL）。 然後，在執行之前，JIT 將 MSIL 編譯成原生機器碼。 如同使用 Unmanaged 程式碼一樣，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。 您也可以用相同的方式設定 JIT 編譯以進行偵錯工具。

JIT 組態有兩個層面：

- 您可以要求 JIT 編譯程式產生追蹤資訊。 這可讓偵錯工具的機器碼對應項目對應上 MSIL 鏈結，追蹤本機變數和函式引數的儲存位置。 從 .NET Framework 版本2.0 開始，JIT 編譯程式一律會產生追蹤資訊，因此不需要要求它。

- 您可以要求 JIT 編譯程式不要將產生的機器程式碼優化。

一般來說，產生 MSIL 的編譯器會根據您指定的 IDE 參數或命令列選項（例如，/**Od**），適當地設定這些 JIT 編譯程式選項。

在某些情況下，您可能想要變更 JIT 編譯器的行為，以便更容易偵錯它產生的機器碼。 例如，您可能想要產生零售組建的 JIT 追蹤資訊，或控制最佳化。 您可以使用初始設定 (.ini) 檔案完成此作業。

例如，如果您想要 debug 的元件稱為*myapp.exe*，則您可以在與*MyApp*相同的資料夾中建立名為*myapp*的文字檔，其中包含下列三行：

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

每個選項的值可以設成 0 或 1，任何不存在的選項預設值皆為 0。 將 `GenerateTrackingInfo` 設為 1、`AllowOptimize` 設為 0，會提供最簡單的偵錯。

從 .NET Framework 版本2.0 開始，JIT 編譯程式一律會產生追蹤資訊，而不論的值`GenerateTrackingInfo`為何; 不過，此`AllowOptimize`值仍然會有作用。 當使用 [Ngen.exe (原生映像產生器)](../tools/ngen-exe-native-image-generator.md) 先行編譯未最佳化的原生映像時，在執行 Ngen.exe 時，.ini 檔案中必須位在目標資料夾中且附有 `AllowOptimize=0`。 如果您已先行編譯不含優化的元件，則必須先使用 Ngen.exe **/uninstall**選項移除先行編譯的程式碼，然後再重新執行 ngen.exe，以將程式碼先行編譯為優化。 如果 .ini 檔案不存在於資料夾中，則 Ngen.exe 預設會將程式碼預先編譯為優化。

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> 控制組件的設定。 **DebuggableAttribute**包含兩個欄位，可控制 JIT 編譯程式是否應該優化和（或）產生追蹤資訊。 從 .NET Framework 版本2.0 開始，JIT 編譯程式一律會產生追蹤資訊。

針對零售組建，編譯器不會設定任何**DebuggableAttribute**。 根據預設，JIT 編譯程式會產生最高效能，而不難進行程式碼的偵錯工具。 啟用 JIT 追蹤會略降低效能，而停用最佳化則會大幅降低效能。

**DebuggableAttribute** 是一次套用至整個組件，不是一一套用到組件中的個別模組。 因此，開發工具必須將自訂屬性附加至組件中繼資料權杖 (如已建立組件)，或附加至稱為 **System.Runtime.CompilerServices.AssemblyAttributesGoHere** 的類別。 然後，ALink 工具會將這些**DebuggableAttribute**屬性從每個模組升級為它們所屬的元件。 如果發生衝突，ALink 作業會失敗。

> [!NOTE]
> 在 .NET Framework 1.0 版中，當指定 **/clr** 和 **/Zi** 編譯器選項時，Microsoft Visual C++ 編譯器會新增 **DebuggableAttribute**。 在1.1 版的 .NET Framework 中，您必須在程式碼中手動新增**DebuggableAttribute** ，或使用 **/ASSEMBLYDEBUG**連結器選項。

## <a name="see-also"></a>另請參閱

- [偵錯、追蹤和程式碼剖析](index.md)
- [啟用 JIT 附加偵錯](enabling-jit-attach-debugging.md)
- [啟用分析](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
