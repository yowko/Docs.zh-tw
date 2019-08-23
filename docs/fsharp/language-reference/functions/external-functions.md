---
title: 外部函式
description: 瞭解在機器碼F#中呼叫函數的語言支援。
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968724"
---
# <a name="external-functions"></a>外部函式

本主題描述F#在機器碼中呼叫函數的語言支援。

## <a name="syntax"></a>語法

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>備註

在先前的語法中,*引數*代表提供給`System.Runtime.InteropServices.DllImportAttribute`屬性的引數。 第一個引數是字串, 代表包含此函式之 DLL 的名稱, 但不含 .dll 副檔名。 可以為`System.Runtime.InteropServices.DllImportAttribute`類別的任何公用屬性提供其他引數, 例如呼叫慣例。

假設您有一個包含C++下列匯出函式的原生 DLL。

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

您可以使用下列程式碼F# , 從呼叫這個函式。

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

與機器碼的互通性稱為「*平台叫用*」, 它是 CLR 的一項功能。 如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../framework/interop/index.md)。 該區段中的資訊適用于F#。

## <a name="see-also"></a>另請參閱

- [函式](index.md)
