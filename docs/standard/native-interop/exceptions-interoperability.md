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
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>在非受控程式碼中使用 Interop 例外狀況

只有在 Windows 平臺上才支援非受控碼例外狀況 interop。 非 Windows 平臺上發生可攜性問題。 因為 Unix ABI 沒有例外狀況處理的定義，所以 managed 程式碼無法得知例外狀況機制在幕後的工作方式。 因此，例外狀況最後可能會導致無法預期的行為，並當機。

## <a name="setjmplongjmp-behaviors"></a>Setjmp/Longjmp 行為

不支援`setjmp`與`longjmp`和 C 函式的 Interop。 您不能`longjmp`使用略過 managed 框架。

如需詳細資訊，請參閱[longjmp 檔](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp)。

## <a name="see-also"></a>另請參閱

- [例外狀況](index.md)
- [使用原生程式庫的 Interop](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
