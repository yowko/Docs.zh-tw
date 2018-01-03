---
title: "MsgBox 範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5dcabfadae35cad980d210806c47dab3f5a0082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="msgbox-sample"></a>MsgBox 範例
此範例示範如何以傳值方式將字串類型傳遞為 In 參數，以及何時使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 和 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> 欄位。  
  
 MsgBox 範例會使用下列 Unmanaged 函式和其原始函式宣告，如下所示：  
  
-   從 User32.dll 匯出的 **MessageBox**。  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 在此範例中，`LibWrap` 類別包含 `MsgBoxSample` 類別所呼叫之每個 Unmanaged 函式的 Managed 原型。 Managed 原型方法 `MsgBox`、`MsgBox2` 和 `MsgBox3` 有相同 Unmanaged 函式的不同宣告。  
  
 `MsgBox2` 的宣告會在訊息方塊中產生不正確的輸出，因為指定為 ANSI 的字元類型與進入點 `MessageBoxW` (即 Unicode 函式的名稱) 不相符。 `MsgBox3` 的宣告會在 **EntryPoint**、**CharSet** 與 **ExactSpelling** 欄位之間建立不相符項目。 呼叫時，`MsgBox3` 會擲回例外狀況。 如需字串命名和名稱封送處理的詳細資訊，請參閱[指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)。  
  
## <a name="declaring-prototypes"></a>宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>請參閱  
 [封送處理字串](../../../docs/framework/interop/marshaling-strings.md)  
 [平台叫用資料類型](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [字串的預設封送處理](../../../docs/framework/interop/default-marshaling-for-strings.md)  
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)
