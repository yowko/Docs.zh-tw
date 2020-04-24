---
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b906178abf8d159083d95e41448596d512e857de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348581"
---
# <a name="-refonly-visual-basic"></a>-refonly （Visual Basic）

**-Refonly**選項指出編譯的主要輸出應該是參考元件，而不是實作為元件。 `-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>語法

```console
-refonly
```

## <a name="remarks"></a>備註

Visual Basic 支援從`-refonly` 15.3 版開始的交換器。

參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最小中繼資料量。 其中包括在建立工具中參考元件時，所有重要成員的宣告，但會排除所有成員的執行，以及對其 API 合約沒有明顯影響的私用成員宣告。 如需詳細資訊，請參閱 .NET 中的[參考元件](../../../standard/assembly/reference-assemblies.md)指南。

`-refonly`和[`-refout`](refout-compiler-option.md)選項互斥。

## <a name="see-also"></a>另請參閱

- [-refout](refout-compiler-option.md)
- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列範例](sample-compilation-command-lines.md)
