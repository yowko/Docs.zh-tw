---
title: End 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: cb2fb4abb21b7b9c6575cec4aca1374f63687607
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343728"
---
# <a name="end-statement"></a>End 陳述式
立即終止執行。  
  
## <a name="syntax"></a>語法  
  
```vb  
End  
```  
  
## <a name="remarks"></a>備註  
 您可以將 `End` 語句放在程式中的任何位置，以強制整個應用程式停止執行。 `End` 關閉任何以 `Open` 語句開啟的檔案，並清除所有應用程式的變數。 應用程式會在沒有任何其他程式持有其物件的參考，而且沒有任何執行中的程式碼時立即關閉。  
  
> [!NOTE]
> `End` 語句會突然停止程式碼執行，而且不會叫用 `Dispose` 或 `Finalize` 方法，或是任何其他 Visual Basic 程式碼。 其他程式所持有的物件參考無效。 如果在 `Try` 或 `Catch` 區塊內遇到 `End` 語句，則控制項不會傳遞至對應的 `Finally` 區塊。  
  
 `Stop` 語句會暫停執行，但與 `End`不同的是，它不會關閉任何檔案或清除任何變數，除非在編譯的可執行檔（.exe）中遇到。  
  
 由於 `End` 會終止您的應用程式，而不會參與任何可能開啟的資源，因此您應該在使用之前，先徹底關閉。 例如，如果您的應用程式開啟了任何表單，您應該先關閉它們，然後再控制到達 `End` 語句。  
  
 您應該謹慎使用 `End`，而且只有在需要立即停止時才會用到。 結束程式（[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)和[Exit 語句](../../../visual-basic/language-reference/statements/exit-statement.md)）的一般方法不只是完全關閉程式，還能讓呼叫程式碼有機會完全關閉。 例如，主控台應用程式可以直接從 `Main` 程式 `Return`。  
  
> [!IMPORTANT]
> `End` 語句會在 <xref:System> 命名空間中呼叫 <xref:System.Environment> 類別的 <xref:System.Environment.Exit%2A> 方法。 <xref:System.Environment.Exit%2A> 需要您具備 `UnmanagedCode` 許可權。 如果不這麼做，就會發生 <xref:System.Security.SecurityException> 錯誤。  
  
 後面接著一個額外的關鍵字時， [end \<關鍵字 > 語句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)會描寫適當程式或區塊定義的結尾。 例如，`End Function` 終止 `Function` 程式的定義。  
  
## <a name="example"></a>範例  
 下列範例會使用 `End` 語句來終止程式碼執行（如果使用者要求）。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援此語句。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop 陳述式](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<關鍵字 > 語句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
