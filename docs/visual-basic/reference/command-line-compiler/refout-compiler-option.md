---
title: -refout （Visual Basic）
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582865"
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

參考元件是僅限中繼資料的元件，其中包含中繼資料，但沒有任何實作為程式碼。 其中包括匿名型別以外所有專案的類型和成員資訊。 其方法主體會取代為單一 `throw null` 語句。 使用 `throw null` 方法主體（而不是任何主體）的原因，是為了讓 PEVerify 能夠執行和傳遞（藉此驗證中繼資料的完整性）。

參考元件包含元件層級的[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。 這個屬性可在來源中指定 (然後編譯器就不需要合成它)。 由於這個屬性，執行時間會拒絕載入參考元件以執行（但仍可在僅限反映的內容中載入）。 在元件上反映的工具必須確保它們將參考元件載入為僅限反映;否則，執行時間會擲回 <xref:System.BadImageFormatException>。

`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。

## <a name="see-also"></a>請參閱

- [-refonly](refonly-compiler-option.md)
- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列範例](sample-compilation-command-lines.md)
