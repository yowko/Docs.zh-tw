---
title: '檔規則 (程式碼分析) '
description: 瞭解程式碼分析規則檔規則
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96585322"
---
# <a name="documentation-rules"></a>文件規則

檔規則支援透過正確使用外部可見 Api 的 [XML 檔批註](../../../csharp/codedoc.md) ，來撰寫妥善記載的程式庫。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1200：請避免使用具有前置詞的 cref 標記](ca1200.md) | XML 檔標記中的 [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) 屬性工作表示「程式碼參考」。 它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。 避免使用具有前置詞的 `cref` 標記，因為它會防止編譯器驗證參考。 它也可防止 Visual Studio 整合式開發環境 (IDE) 在重構期間尋找和更新這些符號參考。 |
