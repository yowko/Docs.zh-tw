---
title: 外部函式 (F#)
description: '深入了解的 F # 語言支援原生程式碼呼叫的函式。'
ms.date: 05/16/2016
ms.openlocfilehash: 398697c5e0deab7f8d81ec5198ab1918bd865e13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564478"
---
# <a name="external-functions"></a>外部函式

本主題描述針對原生程式碼中呼叫函式 F # 語言支援。

## <a name="syntax"></a>語法

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>備註

在先前的語法，*引數*代表引數提供給`System.Runtime.InteropServices.DllImportAttribute`屬性。 第一個引數是字串，代表包含此函式，但不包括.dll 副檔名的 DLL 名稱。 其他引數可以提供任何的公用屬性`System.Runtime.InteropServices.DllImportAttribute`類別，例如呼叫慣例。

假設您有原生 c + + DLL，其中包含下列匯出的函式。

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

您可以使用下列程式碼，從 F # 呼叫此函式。

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

與原生程式碼的互通性指*平台叫用*而且它是 CLR 的功能。 如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)。 在該節中的資訊也適用於 F #。


## <a name="see-also"></a>另請參閱

[函式](index.md)
