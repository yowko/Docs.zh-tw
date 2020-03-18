---
title: 中斷性變更類別
description: 了解 .NET Core 如何分類中斷性變更。
ms.date: 06/10/2019
ms.openlocfilehash: b273ebbb82da803cde66ea34760aa1779c6c1ca5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093041"
---
# <a name="breaking-change-categories"></a>中斷性變更類別

*相容性*是指在實作之 .NET 版本上編譯或執行程式碼的能力，而該版本與原先開發程式碼時所使用的 .NET 版本不同。 特定變更可能會造成六種不同的相容性影響。 評估相容性時考慮[的單個更改類型](index.md)分為以下幾類：

- [行為變化](#behavioral-change)
- [二進位相容性](#binary-compatibility)
- [源相容性](#source-compatibility)
- [設計時相容性](#design-time-compatibility)
- [向後相容性](#backwards-compatibility)
- [正向相容性](#forward-compatibility)（不是 .NET 核心的目標）

## <a name="behavioral-change"></a>行為變更

行為變更表示變更了成員的行為。 這類變更可能會外顯 (例如方法可能會擲回不同的例外狀況)，也可能表示實作變更 (例如變更了傳回值的計算方式、新增或移除了內部方法呼叫，甚至是巨幅地改進了效能)。

當行為變更外顯，並修改了類型的公開合約之後，因為會影響二進位相容性，所以評估這類變更相當容易。 實作變更在評估上則更為困難；而根據變更的性質及 API 的使用頻率與模式，變更所造成的影響可能從嚴重到無害不等。

## <a name="binary-compatibility"></a>二進位相容性

二進位相容性是指 API 消費者無須重新編譯，就能在新版上使用 API 的能力。 諸如新增方法，或為類型新增介面實作一類的變更，都不會影響二進位相容性。 但若是移除或改變組件的公開特徵標記，致使消費者無法再存取組件公開的同一個介面，就會影響二進位相容性。 這類變更稱為*二進位不相容變更*。

## <a name="source-compatibility"></a>來源相容性

來源相容性是指現有 API 消費者無須變更原始程式碼，就能透過新版進行重新編譯的能力。 當消費者必須修原始程式碼，程式碼才能成功透過新版 API 進行建置時，就會發生*來源不相容變更*。

## <a name="design-time-compatibility"></a>設計階段相容性

設計階段相容性是指保留在不同版本 Visual Studio 及其他設計階段環境上之設計階段體驗的能力。 雖然這有可能會涉及設計工具的行為或 UI，但最攸關設計階段相容性的層面，則是專案相容性。 專案或解決方案必須能夠在新版的設計階段環境上開啟及使用。

## <a name="backwards-compatibility"></a>回溯相容性

回溯相容性是指現有 API 消費者對新版執行時，仍能保有相同行為的能力。 行為變更與二進位相容性變更都會影響回溯相容性。 若消費者無法對新版執行，或對新版執行時，無法保有相同的行為，此 API 便是*回溯不相容*。

不鼓勵更改影響向後相容性，因為開發人員期望在 API 的較新版本中向後相容。

## <a name="forward-compatibility"></a>往後相容性

往後相容性是指現有 API 消費者對舊版執行時，仍能保有相同行為的能力。 若消費者無法對舊版執行，或對舊版執行時，無法保有相同的行為，此 API 便是*往後不相容*。

實際上，維護往後相容性可防止版本更迭時變更或新增，因為這些變更會造成使用新版的消費者無法在舊版中執行。 開發人員會預期使用新版 API 的消費者，在對舊版 API 執行時無法正常運作。

.NET Core 不會維護往後相容性。

## <a name="see-also"></a>另請參閱

- [評估 .NET Core 中的中斷性變更](index.md)
