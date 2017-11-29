---
title: "外部函式 (F#)"
description: "深入了解的 F # 語言支援原生程式碼呼叫的函式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c26b6124-ceaa-471c-9dc9-861b4dfa332a
ms.openlocfilehash: 4f525b2b750c2ce42230c61aa0e72f957739b206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="external-functions"></a><span data-ttu-id="dbb8f-104">外部函式</span><span class="sxs-lookup"><span data-stu-id="dbb8f-104">External Functions</span></span>

<span data-ttu-id="dbb8f-105">本主題描述針對原生程式碼中呼叫函式 F # 語言支援。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-105">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbb8f-106">語法</span><span class="sxs-lookup"><span data-stu-id="dbb8f-106">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="dbb8f-107">備註</span><span class="sxs-lookup"><span data-stu-id="dbb8f-107">Remarks</span></span>

<span data-ttu-id="dbb8f-108">在先前的語法，*引數*代表引數提供給`System.Runtime.InteropServices.DllImportAttribute`屬性。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-108">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="dbb8f-109">第一個引數是字串，代表包含此函式，但不包括.dll 副檔名的 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-109">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="dbb8f-110">其他引數可以提供任何的公用屬性`System.Runtime.InteropServices.DllImportAttribute`類別，例如呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-110">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="dbb8f-111">假設您有原生 c + + DLL，其中包含下列匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-111">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="dbb8f-112">您可以使用下列程式碼，從 F # 呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-112">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="dbb8f-113">與原生程式碼的互通性指*平台叫用*而且它是 CLR 的功能。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-113">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="dbb8f-114">如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](https://msdn.microsoft.com/library/sd10k43k.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-114">For more information, see [Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/sd10k43k.aspx).</span></span> <span data-ttu-id="dbb8f-115">在該節中的資訊也適用於 F #。</span><span class="sxs-lookup"><span data-stu-id="dbb8f-115">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="dbb8f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbb8f-116">See Also</span></span>

[<span data-ttu-id="dbb8f-117">函式</span><span class="sxs-lookup"><span data-stu-id="dbb8f-117">Functions</span></span>](index.md)
