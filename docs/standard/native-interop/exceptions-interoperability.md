---
title: 例外狀況互通性
ms.date: 01/16/2020
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: db7c9943c298607aa91a4bd08ddc12bbafc872be
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830619"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>使用非受控碼中的 Interop 例外狀況

僅 Windows 平臺支援非受控碼例外狀況 interop。 非 Windows 平臺會產生可攜性問題。 由於 Unix ABI 沒有例外狀況處理的定義，因此 managed 程式碼無法得知例外狀況機制在幕後的運作方式。 因此，例外狀況最終可能會導致無法預期的行為和當機。

## <a name="setjmplongjmp-behaviors"></a>Setjmp/Longjmp 行為

不支援 Interop 與與 `setjmp` `longjmp` C 函數。 您無法使用 `longjmp` 略過 managed 框架。

如需詳細資訊，請參閱 [longjmp 檔](/cpp/c-runtime-library/reference/longjmp)。

## <a name="see-also"></a>請參閱

- [例外狀況](index.md)
- [使用原生程式庫進行 Interop](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
