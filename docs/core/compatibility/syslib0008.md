---
title: SYSLIB0008 警告
description: 瞭解產生編譯時期警告 SYSLIB0008 的 obsoletion。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440591"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a>SYSLIB0008：不支援 CreatePdbGenerator

<xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>API 已標示為過時，從 .net 5.0 開始。 使用這個 API 會 `SYSLIB0008` 在編譯時期產生警告。

## <a name="suppress-the-warning"></a>隱藏警告

如果您無法變更程式碼，您可以透過指示詞 `#pragma` 或專案設定來隱藏警告 `<NoWarn>` 。 如需範例，請參閱 [隱藏警告](syslib-obsoletions.md#suppress-warnings)。
