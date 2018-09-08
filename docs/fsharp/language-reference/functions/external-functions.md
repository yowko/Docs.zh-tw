---
title: 外部函式 (F#)
description: '深入了解原生程式碼中呼叫函式的 F # 語言支援。'
ms.date: 05/16/2016
ms.openlocfilehash: db0d3362d867b07b333951f3380c6735ff471d5e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181413"
---
# <a name="external-functions"></a><span data-ttu-id="ebccf-103">外部函式</span><span class="sxs-lookup"><span data-stu-id="ebccf-103">External Functions</span></span>

<span data-ttu-id="ebccf-104">本主題說明 F # 語言支援的原生程式碼中呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="ebccf-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebccf-105">語法</span><span class="sxs-lookup"><span data-stu-id="ebccf-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="ebccf-106">備註</span><span class="sxs-lookup"><span data-stu-id="ebccf-106">Remarks</span></span>

<span data-ttu-id="ebccf-107">在先前的語法*引數*代表引數提供給`System.Runtime.InteropServices.DllImportAttribute`屬性。</span><span class="sxs-lookup"><span data-stu-id="ebccf-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="ebccf-108">第一個引數是字串，表示包含此函式，但不包括.dll 副檔名 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="ebccf-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="ebccf-109">其他引數可以提供任何的公用屬性`System.Runtime.InteropServices.DllImportAttribute`類別，例如呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="ebccf-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="ebccf-110">假設您有原生 c + + DLL，其中包含下列匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="ebccf-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="ebccf-111">您可以從 F # 中呼叫此函式，使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="ebccf-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="ebccf-112">與原生程式碼的互通性指*平台叫用*而且它是在 CLR 的功能。</span><span class="sxs-lookup"><span data-stu-id="ebccf-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="ebccf-113">如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ebccf-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="ebccf-114">該節中的資訊適用於 F #。</span><span class="sxs-lookup"><span data-stu-id="ebccf-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebccf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebccf-115">See also</span></span>

- [<span data-ttu-id="ebccf-116">函式</span><span class="sxs-lookup"><span data-stu-id="ebccf-116">Functions</span></span>](index.md)
