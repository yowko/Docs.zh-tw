---
title: 原始碼程式行、檔案與路徑識別項
description: 了解如何使用內建的F#可讓您存取來源的識別碼值行編號、 目錄和檔案名稱，在您的程式碼。
ms.date: 05/16/2016
ms.openlocfilehash: 4b145fe1fe20e3d7f868558e33bab26204fb0125
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656007"
---
# <a name="source-line-file-and-path-identifiers"></a>原始碼程式行、檔案與路徑識別項

識別項`__LINE__`，`__SOURCE_DIRECTORY__`和`__SOURCE_FILE__`內建值可讓您存取您的程式碼的來源行號、 目錄和檔案名稱。

## <a name="syntax"></a>語法

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>備註

每個這些值都有型別`string`。

下表摘要說明中所提供的來源行、 檔案和路徑識別碼F#。 這些識別項不是前置處理器巨集;它們是編譯器可辨識的內建值。

|預先定義的識別項|描述|
|---------------------|-----------|
|`__LINE__`|評估為目前的行號，考慮`#line`指示詞。|
|`__SOURCE_DIRECTORY__`|評估為目前的完整路徑的來源目錄中，考慮`#line`指示詞。|
|`__SOURCE_FILE__`|評估為目前的來源檔案名稱和其路徑中，考慮`#line`指示詞。|

如需詳細資訊`#line`指示詞，請參閱[編譯器指示詞](compiler-directives.md)。

## <a name="example"></a>範例

下列程式碼範例示範如何使用這些值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

輸出：

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>另請參閱

- [編譯器指示詞](compiler-directives.md)
- [F# 語言參考](index.md)
