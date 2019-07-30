---
title: 原始碼程式行、檔案與路徑識別項
description: 瞭解如何使用內F#建的識別碼值, 讓您存取程式碼中的原始程式列號、目錄和檔案名。
ms.date: 05/16/2016
ms.openlocfilehash: 5ff36210edc75370f8baf9ee7be057f3ac0c3979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627111"
---
# <a name="source-line-file-and-path-identifiers"></a>原始碼程式行、檔案與路徑識別項

識別碼`__LINE__` `__SOURCE_DIRECTORY__`和是內建值,可讓您存取程式碼中的原始程式列號、目錄和檔案名。`__SOURCE_FILE__`

## <a name="syntax"></a>語法

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>備註

這些值的每一個都`string`具有類型。

下表摘要說明中F#可用的原始程式列、檔案和路徑識別碼。 這些識別碼不是預處理器宏;這些是編譯器可辨識的內建值。

|預先定義的識別碼|描述|
|---------------------|-----------|
|`__LINE__`|評估為目前的行號, 並`#line`考慮指示詞。|
|`__SOURCE_DIRECTORY__`|評估為來原始目錄的目前完整路徑, 並考慮`#line`指示詞。|
|`__SOURCE_FILE__`|評估為目前的來原始檔案名, 不含其路徑, 考慮`#line`指示詞。|

如需指示詞的`#line`詳細資訊, 請參閱[編譯器](compiler-directives.md)指示詞。

## <a name="example"></a>範例

下列程式碼範例示範如何使用這些值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

輸出：

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>另請參閱

- [編譯器指示詞](compiler-directives.md)
- [F# 語言參考](index.md)
