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
# <a name="external-functions"></a><span data-ttu-id="07598-103">外部函式</span><span class="sxs-lookup"><span data-stu-id="07598-103">External Functions</span></span>

<span data-ttu-id="07598-104">本主題描述針對原生程式碼中呼叫函式 F # 語言支援。</span><span class="sxs-lookup"><span data-stu-id="07598-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="07598-105">語法</span><span class="sxs-lookup"><span data-stu-id="07598-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="07598-106">備註</span><span class="sxs-lookup"><span data-stu-id="07598-106">Remarks</span></span>

<span data-ttu-id="07598-107">在先前的語法，*引數*代表引數提供給`System.Runtime.InteropServices.DllImportAttribute`屬性。</span><span class="sxs-lookup"><span data-stu-id="07598-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="07598-108">第一個引數是字串，代表包含此函式，但不包括.dll 副檔名的 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="07598-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="07598-109">其他引數可以提供任何的公用屬性`System.Runtime.InteropServices.DllImportAttribute`類別，例如呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="07598-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="07598-110">假設您有原生 c + + DLL，其中包含下列匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="07598-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="07598-111">您可以使用下列程式碼，從 F # 呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="07598-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="07598-112">與原生程式碼的互通性指*平台叫用*而且它是 CLR 的功能。</span><span class="sxs-lookup"><span data-stu-id="07598-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="07598-113">如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="07598-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="07598-114">在該節中的資訊也適用於 F #。</span><span class="sxs-lookup"><span data-stu-id="07598-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="07598-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07598-115">See Also</span></span>

[<span data-ttu-id="07598-116">函式</span><span class="sxs-lookup"><span data-stu-id="07598-116">Functions</span></span>](index.md)
