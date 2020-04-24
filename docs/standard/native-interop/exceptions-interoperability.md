---
title: 例外狀況互通性
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 2aff71e97e1be0dbb584f4fe43c322cea86d2480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795172"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="600e0-102">在非受控程式碼中使用 Interop 例外狀況</span><span class="sxs-lookup"><span data-stu-id="600e0-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="600e0-103">只有在 Windows 平臺上才支援非受控碼例外狀況 interop。</span><span class="sxs-lookup"><span data-stu-id="600e0-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="600e0-104">非 Windows 平臺上發生可攜性問題。</span><span class="sxs-lookup"><span data-stu-id="600e0-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="600e0-105">因為 Unix ABI 沒有例外狀況處理的定義，所以 managed 程式碼無法得知例外狀況機制在幕後的工作方式。</span><span class="sxs-lookup"><span data-stu-id="600e0-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="600e0-106">因此，例外狀況最後可能會導致無法預期的行為，並當機。</span><span class="sxs-lookup"><span data-stu-id="600e0-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="600e0-107">Setjmp/Longjmp 行為</span><span class="sxs-lookup"><span data-stu-id="600e0-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="600e0-108">不支援`setjmp`與`longjmp`和 C 函式的 Interop。</span><span class="sxs-lookup"><span data-stu-id="600e0-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="600e0-109">您不能`longjmp`使用略過 managed 框架。</span><span class="sxs-lookup"><span data-stu-id="600e0-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="600e0-110">如需詳細資訊，請參閱[longjmp 檔](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp)。</span><span class="sxs-lookup"><span data-stu-id="600e0-110">For more information, see [longjmp documentation](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="600e0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="600e0-111">See also</span></span>

- [<span data-ttu-id="600e0-112">例外狀況</span><span class="sxs-lookup"><span data-stu-id="600e0-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="600e0-113">使用原生程式庫的 Interop</span><span class="sxs-lookup"><span data-stu-id="600e0-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
