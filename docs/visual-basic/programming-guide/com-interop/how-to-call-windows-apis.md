---
title: 如何：呼叫 Windows API
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 9de9f0fbcca291af0b6aadfd8e3fe7033708fbc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347537"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>如何：呼叫 Windows API (Visual Basic)
這個範例會定義並呼叫 user32 中的 `MessageBox` 函式，然後將字串傳遞給它。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System> 命名空間的參考。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 以下條件可能會造成例外狀況：  
  
- 方法不是靜態、是抽象，或先前已定義過。 父類型是介面，或*名稱*或*dllName*的長度為零。 (<xref:System.ArgumentException>)  
  
- *名稱*或*dllName*是 `Nothing`。 (<xref:System.ArgumentNullException>)  
  
- 之前已使用 `CreateType` 建立包含類型。 (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>請參閱

- [詳述平台叫用](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [平台叫用範例](../../../framework/interop/platform-invoke-examples.md)
- [使用 Unmanaged DLL 函式](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [使用反映發出定義方法](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
