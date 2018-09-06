---
title: 外部函式 (F#)
description: '深入了解原生程式碼中呼叫函式的 F # 語言支援。'
ms.date: 05/16/2016
ms.openlocfilehash: db0d3362d867b07b333951f3380c6735ff471d5e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747378"
---
# <a name="external-functions"></a>外部函式

本主題說明 F # 語言支援的原生程式碼中呼叫函式。

## <a name="syntax"></a>語法

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>備註

在先前的語法*引數*代表引數提供給`System.Runtime.InteropServices.DllImportAttribute`屬性。 第一個引數是字串，表示包含此函式，但不包括.dll 副檔名 DLL 的名稱。 其他引數可以提供任何的公用屬性`System.Runtime.InteropServices.DllImportAttribute`類別，例如呼叫慣例。

假設您有原生 c + + DLL，其中包含下列匯出的函式。

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

您可以從 F # 中呼叫此函式，使用下列程式碼。

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

與原生程式碼的互通性指*平台叫用*而且它是在 CLR 的功能。 如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)。 該節中的資訊適用於 F #。

## <a name="see-also"></a>另請參閱

- [函式](index.md)
