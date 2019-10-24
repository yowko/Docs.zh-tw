---
title: -refout （Visual Basic）
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775554"
---
# <a name="-refout-visual-basic"></a>-refout （Visual Basic）

**-refout** 選項指定參考組件應該輸出的檔案路徑。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>語法

```console
-refout:filepath
```

## <a name="arguments"></a>引數

`filepath`  
參考元件的路徑和檔案名。 它通常應該位於主要元件的子資料夾中。 建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。 @No__t_0 中的所有資料夾都必須存在;編譯器不會建立它們。

## <a name="remarks"></a>備註

Visual Basic 支援從15.3 版開始的 `-refout` 交換器。

參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最小中繼資料量。 其中包括在建立工具中參考元件時，所有重要成員的宣告，但會排除所有成員的執行，以及對其 API 合約沒有明顯影響的私用成員宣告。 如需詳細資訊，請參閱 .NET 中的[參考元件](../../../standard/assembly/reference-assemblies.md)指南。

`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。

## <a name="see-also"></a>請參閱

- [-refonly](refonly-compiler-option.md)
- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列範例](sample-compilation-command-lines.md)
