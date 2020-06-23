---
title: MsgBox 範例
description: 請參閱使用 MsgBox 以參數形式傳遞字串類型的範例。 它會顯示在 .NET 中使用 EntryPoint、字元集和 ExactSpelling 欄位的時機。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: ccf882e1f801dd18e5b65a4279fc580d927dd29d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904087"
---
# <a name="msgbox-sample"></a>MsgBox 範例
此範例示範如何以傳值方式將字串類型傳遞為 In 參數，以及何時使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 和 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> 欄位。  
  
 MsgBox 範例會使用下列 Unmanaged 函式和其原始函式宣告，如下所示：  
  
- 從 User32.dll 匯出的 **MessageBox**。  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 在此範例中，`NativeMethods` 類別包含 `MsgBoxSample` 類別所呼叫之每個 Unmanaged 函式的 Managed 原型。 Managed 原型方法 `MsgBox`、`MsgBox2` 和 `MsgBox3` 有相同 Unmanaged 函式的不同宣告。  
  
 `MsgBox2` 的宣告會在訊息方塊中產生不正確的輸出，因為指定為 ANSI 的字元類型與進入點 `MessageBoxW` (即 Unicode 函式的名稱) 不相符。 `MsgBox3` 的宣告會在 **EntryPoint**、**CharSet** 與 **ExactSpelling** 欄位之間建立不相符項目。 呼叫時，`MsgBox3` 會擲回例外狀況。 如需字串命名和名稱封送處理的詳細資訊，請參閱[指定字元集](specifying-a-character-set.md)。  
  
## <a name="declaring-prototypes"></a>宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [封送處理字串](marshaling-strings.md)
- [字串的預設封送處理](default-marshaling-for-strings.md)
- [在 Managed 程式碼中建立原型](creating-prototypes-in-managed-code.md)
- [指定字元集](specifying-a-character-set.md)
