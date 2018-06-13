---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653042"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

**-Refonly**選項表示編譯的主要輸出應為而不是實作組件的參考組件。 `-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>語法

```console
-refonly
```

## <a name="remarks"></a>備註

Visual Basic 支援`-refout`切換版 15.3 開頭。

參考組件是僅中繼資料的組件包含中繼資料但沒有實作程式碼。 它們包含匿名型別以外的所有項目型別和成員資訊。 使用 `throw null` 主體的原因 (相對於沒有主體)，是這樣 PEVerify 便可執行和傳遞 (因此驗證中繼資料的完整性)。

參考組件包含組件層級[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。 這個屬性可在來源中指定 (然後編譯器就不需要合成它)。 這個屬性，因為執行階段將會拒絕載入參考組件的執行 （但仍可以載入僅限反映的內容中）。 反映的組件的工具需要以確保它們載入參考組件做為僅限反映的;否則，執行階段會擲回<xref:System.BadImageFormatException>。

`-refonly` 和 [`-refout`](refout-compiler-option.md) 選項互斥。

## <a name="see-also"></a>另請參閱
[-refout](refout-compiler-option.md)   
[Visual Basic 命令列編譯器](index.md)  
[編譯命令列範例](sample-compilation-command-lines.md)   
