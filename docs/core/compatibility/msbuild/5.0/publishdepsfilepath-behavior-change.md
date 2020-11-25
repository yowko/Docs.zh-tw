---
title: 重大變更： PublishDepsFilePath 行為變更
description: 瞭解 .NET 5.0 中的重大變更，其中單一檔案應用程式的 PublishDepsFilePath MSBuild 屬性是空的。
ms.date: 09/17/2020
ms.openlocfilehash: 70631beff31aa3388e59f3b79875ef437351451a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760806"
---
# <a name="publishdepsfilepath-behavior-change"></a>PublishDepsFilePath 行為變更

`PublishDepsFilePath`單一檔案應用程式的 MSBuild 屬性是空的。 此外，針對非單一檔案的應用程式，在稍後的組建中，檔案 *上的deps.js* 可能不會複製到輸出目錄。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

在舊版的 .NET 中， `PublishDepsFilePath` MSBuild 屬性是應用程式在非單一檔案應用程式輸出目錄中的 *deps.js* 檔案路徑，以及單一檔案應用程式之中繼目錄中的路徑。

從 .NET 5.0 開始， `PublishDepsFilePath` 單一檔案應用程式是空的，而新的 `IntermediateDepsFilePath` 屬性會指定中繼目錄中位置 *上的deps.js* 。 此外，對於非單一檔案應用程式，檔案 *上的deps.js* 可能不會複製到輸出目錄， (也就是) 指定的路徑， `PublishDepsFilePath` 直到稍後在組建中為止。

## <a name="reason-for-change"></a>變更的原因

這項變更的原因有幾個：

- 由於發佈邏輯的重構，可支援在 .NET 5 中 [改善的單一檔案應用程式](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) 。

- 在單一檔案應用程式中，為了防止在 *deps.js開啟* 後嘗試重寫檔案 *deps.js* 的目標，因此不會以無訊息方式影響應用程式。 基於這個理由， `PublishDepsFilePath` 單一檔案應用程式是空的。

## <a name="recommended-action"></a>建議的動作

*在檔案上* 重寫deps.js的目標通常應該使用屬性來進行 `IntermediateDepsFilePath` 。

## <a name="affected-apis"></a>受影響的 API

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
