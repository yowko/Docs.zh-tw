---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: f2cdd228d8ce1912abbbe888c29c42f29299ebba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832732"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**-refout** 選項指定參考組件應該輸出的檔案路徑。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>語法

```console
-refout:filepath
```

## <a name="arguments"></a>引數

 `filepath` 路徑和檔案名稱的參考組件。 它通常應該是主要組件的子資料夾中。 建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。 中的所有資料夾`filepath`必須存在，編譯器不會建立它們。 

## <a name="remarks"></a>備註

Visual Basic 支援`-refout`切換 15.3 版開始。

參考組件是僅中繼資料的組件包含中繼資料，但沒有實作程式碼。 它們包含匿名型別以外的所有項目的型別和成員資訊。 其方法主體取代單一`throw null`陳述式。 使用的原因`throw null`（相對於沒有主體） 的方法主體是這樣 PEVerify 可以執行，並傳遞 （因此驗證中繼資料的完整性）。

參考組件包含組件層級[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。 這個屬性可在來源中指定 (然後編譯器就不需要合成它)。 因為此屬性中，執行階段會拒絕載入參考組件的執行 （但仍可載入僅限反映的內容中）。 在組件反映的工具需要確保它們載入參考組件為僅限反映的;否則，執行階段會擲回<xref:System.BadImageFormatException>。

`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。

## <a name="see-also"></a>另請參閱

- [-refonly](refonly-compiler-option.md)
- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列範例](sample-compilation-command-lines.md)
