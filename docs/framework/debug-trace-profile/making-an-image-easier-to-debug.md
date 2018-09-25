---
title: 使您更輕鬆地在.NET 中偵錯映像
description: 了解如何使用 IDE 更容易偵錯切換設定可執行映像，以及命令列選項。
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f25eaaa17d4c4bd2e9522591bb0fd66445cdb6f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075577"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>使您更輕鬆地在.NET 中偵錯映像

當編譯 Unmanaged 程式碼時，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。 例如，您可以在 Visual C++ 中使用 /**Zi** 命令列選項，要求它發出偵錯符號檔 (副檔名為 .pdb)。 同樣地，/**Od** 命令列選項會通知編譯器停用最佳化。 產生的程式碼的執行速度較慢，但很容易偵錯，要是此為必要。

當編譯.NET Framework managed 程式碼時，例如 Visual c + +、 Visual Basic 和 C# 編譯器會其原始程式編譯成 Microsoft 中間語言 (MSIL)。 MSIL 就 JIT 編譯，剛好執行前，為原生機器碼。 如同使用 Unmanaged 程式碼一樣，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。 您也可以設定相同的方式中的偵錯 JIT 編譯。

JIT 組態有兩個層面：

- 您可以要求 JIT 編譯器產生追蹤資訊。 這可讓偵錯工具的機器碼對應項目對應上 MSIL 鏈結，追蹤本機變數和函式引數的儲存位置。 從.NET Framework 2.0 版開始，JIT 編譯器一律會產生追蹤資訊，這樣就不需要提出要求。

- 您可以要求 JIT 編譯器不要最佳化產生的機器碼。

一般來說，產生 MSIL 的編譯器這些 JIT 編譯器選項適當設定，根據 IDE 參數或命令列指定的選項，例如 /**Od**。

在某些情況下，您可能想要變更 JIT 編譯器的行為，以便更容易偵錯它產生的機器碼。 例如，您可能想要產生零售組建的 JIT 追蹤資訊，或控制最佳化。 您可以使用初始設定 (.ini) 檔案完成此作業。

比方說，如果您想要偵錯的組件稱為*MyApp.exe*，然後您可以建立名為文字檔*MyApp.ini*，在相同的資料夾*MyApp.exe*，其中包含這三行：

```txt
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

每個選項的值可以設成 0 或 1，任何不存在的選項預設值皆為 0。 將 `GenerateTrackingInfo` 設為 1、`AllowOptimize` 設為 0，會提供最簡單的偵錯。

從.NET Framework 2.0 版開始，JIT 編譯器一律會產生追蹤資訊的值為何`GenerateTrackingInfo`; 不過，`AllowOptimize`值仍然沒有作用。 當使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 先行編譯未最佳化的原生映像時，在執行 Ngen.exe 時，.ini 檔案中必須位在目標資料夾中且附有 `AllowOptimize=0`。 如果您有先行編譯未最佳化的組件，您必須移除先行編譯的程式碼使用 NGen.exe **/uninstall**再重新執行 Ngen.exe 先行編譯的程式碼，因為最佳化的選項。 如果.ini 檔案不存在的資料夾中，依預設 Ngen.exe 先行編譯的程式碼因為最佳化。

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> 控制組件的設定。 **DebuggableAttribute** JIT 編譯器應該最佳化及/或產生追蹤資訊是否包含兩個欄位的控制項。 從.NET Framework 2.0 版開始，JIT 編譯器一律會產生追蹤資訊。

零售組建中，編譯器不需要設定任何**DebuggableAttribute**。 根據預設，JIT 編譯器會產生最高的效能，幾乎不偵錯機器碼。 啟用 JIT 追蹤會略降低效能，而停用最佳化則會大幅降低效能。

**DebuggableAttribute** 是一次套用至整個組件，不是一一套用到組件中的個別模組。 因此，開發工具必須將自訂屬性附加至組件中繼資料權杖 (如已建立組件)，或附加至稱為 **System.Runtime.CompilerServices.AssemblyAttributesGoHere** 的類別。 ALink 工具然後升級這些**DebuggableAttribute**從每個模組至組件的屬性成為的一部分。 如果沒有衝突，ALink 作業失敗。

> [!NOTE]
> 在 .NET Framework 1.0 版中，當指定 **/clr** 和 **/Zi** 編譯器選項時，Microsoft Visual C++ 編譯器會新增 **DebuggableAttribute**。 在 .NET Framework 1.1 版中，您必須在程式碼中手動新增 **DebugabbleAttribute**，或使用 **/ASSEMBLYDEBUG** 連結器選項。

## <a name="see-also"></a>另請參閱

- [偵錯、追蹤和程式碼剖析](../../../docs/framework/debug-trace-profile/index.md)
- [啟用 JIT 附加偵錯](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)
- [啟用分析](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
