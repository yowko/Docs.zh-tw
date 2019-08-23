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
# <a name="external-functions"></a><span data-ttu-id="e6d35-103">外部函式</span><span class="sxs-lookup"><span data-stu-id="e6d35-103">External Functions</span></span>

<span data-ttu-id="e6d35-104">本主題描述F#在機器碼中呼叫函數的語言支援。</span><span class="sxs-lookup"><span data-stu-id="e6d35-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6d35-105">語法</span><span class="sxs-lookup"><span data-stu-id="e6d35-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="e6d35-106">備註</span><span class="sxs-lookup"><span data-stu-id="e6d35-106">Remarks</span></span>

<span data-ttu-id="e6d35-107">在先前的語法中,*引數*代表提供給`System.Runtime.InteropServices.DllImportAttribute`屬性的引數。</span><span class="sxs-lookup"><span data-stu-id="e6d35-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="e6d35-108">第一個引數是字串, 代表包含此函式之 DLL 的名稱, 但不含 .dll 副檔名。</span><span class="sxs-lookup"><span data-stu-id="e6d35-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="e6d35-109">可以為`System.Runtime.InteropServices.DllImportAttribute`類別的任何公用屬性提供其他引數, 例如呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="e6d35-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="e6d35-110">假設您有一個包含C++下列匯出函式的原生 DLL。</span><span class="sxs-lookup"><span data-stu-id="e6d35-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="e6d35-111">您可以使用下列程式碼F# , 從呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="e6d35-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="e6d35-112">與機器碼的互通性稱為「*平台叫用*」, 它是 CLR 的一項功能。</span><span class="sxs-lookup"><span data-stu-id="e6d35-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="e6d35-113">如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../framework/interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e6d35-113">For more information, see [Interoperating with Unmanaged Code](../../../framework/interop/index.md).</span></span> <span data-ttu-id="e6d35-114">該區段中的資訊適用于F#。</span><span class="sxs-lookup"><span data-stu-id="e6d35-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6d35-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6d35-115">See also</span></span>

- [<span data-ttu-id="e6d35-116">函式</span><span class="sxs-lookup"><span data-stu-id="e6d35-116">Functions</span></span>](index.md)
