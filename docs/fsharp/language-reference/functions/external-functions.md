---
title: 外部函式 (F#)
description: '深入了解的 F # 語言支援原生程式碼呼叫的函式。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 28e74258d91ff2d9742caa7a6c06f515cd987c0a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="external-functions"></a><span data-ttu-id="276aa-103">外部函式</span><span class="sxs-lookup"><span data-stu-id="276aa-103">External Functions</span></span>

<span data-ttu-id="276aa-104">本主題描述針對原生程式碼中呼叫函式 F # 語言支援。</span><span class="sxs-lookup"><span data-stu-id="276aa-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="276aa-105">語法</span><span class="sxs-lookup"><span data-stu-id="276aa-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="276aa-106">備註</span><span class="sxs-lookup"><span data-stu-id="276aa-106">Remarks</span></span>

<span data-ttu-id="276aa-107">在先前的語法，*引數*代表引數提供給`System.Runtime.InteropServices.DllImportAttribute`屬性。</span><span class="sxs-lookup"><span data-stu-id="276aa-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="276aa-108">第一個引數是字串，代表包含此函式，但不包括.dll 副檔名的 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="276aa-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="276aa-109">其他引數可以提供任何的公用屬性`System.Runtime.InteropServices.DllImportAttribute`類別，例如呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="276aa-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="276aa-110">假設您有原生 c + + DLL，其中包含下列匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="276aa-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="276aa-111">您可以使用下列程式碼，從 F # 呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="276aa-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="276aa-112">與原生程式碼的互通性指*平台叫用*而且它是 CLR 的功能。</span><span class="sxs-lookup"><span data-stu-id="276aa-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="276aa-113">如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="276aa-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="276aa-114">在該節中的資訊也適用於 F #。</span><span class="sxs-lookup"><span data-stu-id="276aa-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="276aa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="276aa-115">See Also</span></span>

[<span data-ttu-id="276aa-116">函式</span><span class="sxs-lookup"><span data-stu-id="276aa-116">Functions</span></span>](index.md)
