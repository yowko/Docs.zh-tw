---
title: 例外狀況互通性
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 90774b5d1b64feb34e01f48708d94f8f841a7c9d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550868"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="feb9f-102">使用非受控碼中的 Interop 例外狀況</span><span class="sxs-lookup"><span data-stu-id="feb9f-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="feb9f-103">僅 Windows 平臺支援非受控碼例外狀況 interop。</span><span class="sxs-lookup"><span data-stu-id="feb9f-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="feb9f-104">非 Windows 平臺會產生可攜性問題。</span><span class="sxs-lookup"><span data-stu-id="feb9f-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="feb9f-105">由於 Unix ABI 沒有例外狀況處理的定義，因此 managed 程式碼無法得知例外狀況機制在幕後的運作方式。</span><span class="sxs-lookup"><span data-stu-id="feb9f-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="feb9f-106">因此，例外狀況最終可能會導致無法預期的行為和當機。</span><span class="sxs-lookup"><span data-stu-id="feb9f-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="feb9f-107">Setjmp/Longjmp 行為</span><span class="sxs-lookup"><span data-stu-id="feb9f-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="feb9f-108">不支援 Interop 與與 `setjmp` `longjmp` C 函數。</span><span class="sxs-lookup"><span data-stu-id="feb9f-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="feb9f-109">您無法使用 `longjmp` 略過 managed 框架。</span><span class="sxs-lookup"><span data-stu-id="feb9f-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="feb9f-110">如需詳細資訊，請參閱 [longjmp 檔](/cpp/c-runtime-library/reference/longjmp)。</span><span class="sxs-lookup"><span data-stu-id="feb9f-110">For more information, see [longjmp documentation](/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="feb9f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feb9f-111">See also</span></span>

- [<span data-ttu-id="feb9f-112">例外狀況</span><span class="sxs-lookup"><span data-stu-id="feb9f-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="feb9f-113">使用原生程式庫進行 Interop</span><span class="sxs-lookup"><span data-stu-id="feb9f-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
