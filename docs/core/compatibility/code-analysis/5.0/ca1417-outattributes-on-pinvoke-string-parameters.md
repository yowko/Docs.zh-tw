---
title: 重大變更： P/Invoke 的字串參數上的 CA1417： OutAttribute
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA1417 所造成的重大變更。
ms.date: 09/29/2020
ms.openlocfilehash: 3316d07108ec7f9da985494413336cba6d560dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760432"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a>警告 CA1417： P/Invoke 的字串參數上的 OutAttribute

預設會啟用 .NET 程式碼分析器規則 [CA1417](/visualstudio/code-quality/ca1417) ，從 .net 5.0 開始。 它會產生任何平台叫用的組建警告 [ (P/Invoke) ](../../../../standard/native-interop/pinvoke.md) 方法定義，其中 <xref:System.String> 參數是以傳值方式傳遞，並以標記 <xref:System.Runtime.InteropServices.OutAttribute> 。

## <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。 預設會啟用這些規則中的數個，包括 [CA1417](/visualstudio/code-quality/ca1417)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

規則 CA1417 會旗標 [P/Invoke](../../../../standard/native-interop/pinvoke.md) 方法定義，其中 <xref:System.String> 參數標記為 <xref:System.Runtime.InteropServices.OutAttribute> 屬性，並以傳值方式傳遞。 例如：

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

.NET 執行時間會維護名為實習集區的資料表，其中包含程式中每個唯一常值字串的單一參考。 如果以傳值方式將標記為的留用字串 <xref:System.Runtime.InteropServices.OutAttribute> 以傳值方式傳遞至 P/Invoke 方法，則可以 destabilized 執行時間。 如需有關字串暫留的詳細資訊，請參閱的備註 <xref:System.String.Intern(System.String)?displayProperty=nameWithType> 。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

- 如果您需要將修改過的字串資料封送處理回呼叫端，請改以傳址方式傳遞字串。

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- 如果您不需要將修改過的字串資料封送處理回呼叫端，只要移除 <xref:System.Runtime.InteropServices.OutAttribute> 。

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  如需詳細資訊，請參閱 [CA1417](/visualstudio/code-quality/ca1417)。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。

## <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
