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
ms.openlocfilehash: 0c99b919b50701e93fab7caf5fb5d8b6b976d44b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865855"
---
# <a name="end-statement"></a>End 陳述式

立即終止執行。  
  
## <a name="syntax"></a>語法  
  
```vb  
End  
```  
  
## <a name="remarks"></a>備註  

 您可以將 `End` 語句放在程式中的任何位置，以強制整個應用程式停止執行。 `End` 關閉任何以語句開啟的檔案 `Open` ，並清除所有應用程式的變數。 只要沒有任何其他程式保留其物件的參考，而且沒有任何程式碼正在執行時，應用程式就會關閉。  
  
> [!NOTE]
> `End`語句會突然停止執行程式碼，而不會叫用 `Dispose` 或 `Finalize` 方法，或任何其他 Visual Basic 程式碼。 其他程式所持有的物件參考無效。 如果在 `End` 或區塊中遇到語句 `Try` `Catch` ，控制項就不會傳遞至對應的 `Finally` 區塊。  
  
 `Stop`語句會暫停執行，但與不同的 `End` 是，它不會關閉任何檔案或清除任何變數，除非在編譯的可執行檔 ( .exe) 檔中遇到。  
  
 由於您 `End` 的應用程式會在不參與任何可能開啟的資源的情況下終止，所以您應該嘗試在使用之前先徹底關閉。 例如，如果您的應用程式已開啟任何表單，您應該在控制權到達語句之前將其關閉 `End` 。  
  
 您應該 `End` 謹慎使用，而且只有在需要立即停止時才需要。 終止程式 (傳回 [語句](return-statement.md) 和結束 [語句](exit-statement.md) 的一般方式，) 不僅能完全關閉程式，還可讓呼叫程式碼有機會完全關閉。 例如，主控台應用程式可以直接從程式 `Return` 中取得 `Main` 。  
  
> [!IMPORTANT]
> `End`語句會呼叫 <xref:System.Environment.Exit%2A> <xref:System.Environment> 命名空間中類別的方法 <xref:System> 。 <xref:System.Environment.Exit%2A> 需要您具備 `UnmanagedCode` 許可權。 如果沒有， <xref:System.Security.SecurityException> 就會發生錯誤。  
  
 當後面加上其他關鍵字時， [end \<keyword> 語句](end-keyword-statement.md) 會描述適當程式或區塊的定義結尾。 例如， `End Function` 結束程式的定義 `Function` 。  
  
## <a name="example"></a>範例  

 下列範例 `End` 會使用語句來終止程式碼執行（如果使用者要求的話）。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  

 不支援此陳述式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop 陳述式](stop-statement.md)
- [End \<keyword> 語句](end-keyword-statement.md)
