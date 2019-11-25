---
title: 如何：呼叫 Windows API
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 6f3c53243d7aeb73be81796d5ca185c3a3c41c72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348705"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>如何：呼叫 Windows API (Visual Basic)
This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System> 命名空間的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
- The method is not static, is abstract, or has been previously defined. The parent type is an interface, or the length of *name* or *dllName* is zero. (<xref:System.ArgumentException>)  
  
- The *name* or *dllName* is `Nothing`. (<xref:System.ArgumentNullException>)  
  
- 之前已使用 `CreateType` 建立包含類型。 (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>請參閱

- [詳述平台叫用](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [平台叫用範例](../../../framework/interop/platform-invoke-examples.md)
- [使用 Unmanaged DLL 函式](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
