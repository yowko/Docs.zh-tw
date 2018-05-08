---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21cea76f31bdf2ac5fcf434ee759f874f917617b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**-refout** 選項指定參考組件應該輸出的檔案路徑。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>語法

```console
-refout:filepath
```

## <a name="arguments"></a>引數

 `filepath` 路徑和檔案名稱的參考組件。 它通常應該在主要組件的子資料夾。 建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。 中的所有資料夾`filepath`必須存在，編譯器不會建立它們。 

## <a name="remarks"></a>備註

Visual Basic 支援`-refout`切換版 15.3 開頭。

參考組件是僅中繼資料的組件包含中繼資料但沒有實作程式碼。 它們包含匿名型別以外的所有項目型別和成員資訊。 其方法主體就會取代單一`throw null`陳述式。 使用的原因`throw null`（而不是沒有內文） 的方法主體，以便 PEVerify 可以執行和傳遞 （因此驗證中繼資料的完整性）。

參考組件包含組件層級[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。 這個屬性可在來源中指定 (然後編譯器就不需要合成它)。 這個屬性，因為執行階段拒絕載入參考組件的執行 （但仍可以載入僅限反映的內容中）。 反映的組件的工具需要以確保它們載入參考組件做為僅限反映的;否則，執行階段會擲回<xref:System.BadImageFormatException>。

`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。

## <a name="see-also"></a>另請參閱
[-refonly](refonly-compiler-option.md)   
[Visual Basic 命令列編譯器](index.md)  
[編譯命令列範例](sample-compilation-command-lines.md)  

