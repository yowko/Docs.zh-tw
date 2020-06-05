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
ms.openlocfilehash: fe17a82662c4014069c77f2da76723a051ab9084
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404702"
---
# <a name="end-statement"></a>End 陳述式
立即終止執行。  
  
## <a name="syntax"></a>語法  
  
```vb  
End  
```  
  
## <a name="remarks"></a>備註  
 您可以將 `End` 語句放在程式中的任何位置，以強制整個應用程式停止執行。 `End`關閉任何以語句開啟的檔案 `Open` ，並清除所有應用程式的變數。 應用程式會在沒有任何其他程式持有其物件的參考，而且沒有任何執行中的程式碼時立即關閉。  
  
> [!NOTE]
> `End`語句會突然停止程式碼執行，而且不會叫用 `Dispose` 或 `Finalize` 方法，或是任何其他 Visual Basic 程式碼。 其他程式所持有的物件參考無效。 如果 `End` 在或區塊內遇到語句 `Try` `Catch` ，則控制項不會傳遞至對應的 `Finally` 區塊。  
  
 `Stop`語句會暫停執行，但與不同的 `End` 是，它不會關閉任何檔案或清除任何變數，除非在編譯的可執行檔（.exe）中遇到此錯誤。  
  
 由於會 `End` 終止您的應用程式，而不會參與任何可能開啟的資源，因此您應該在使用之前，先徹底關閉。 例如，如果您的應用程式開啟了任何表單，您應該先關閉它們，然後再控制到達 `End` 語句。  
  
 您應該 `End` 謹慎使用，而且只有在需要立即停止時才會用到。 結束程式（[Return 語句](return-statement.md)和[Exit 語句](exit-statement.md)）的一般方法不只是完全關閉程式，還能讓呼叫程式碼有機會完全關閉。 例如，主控台應用程式可以只從程式 `Return` 中進行 `Main` 。  
  
> [!IMPORTANT]
> `End`語句會 <xref:System.Environment.Exit%2A> <xref:System.Environment> 在命名空間中呼叫類別的方法 <xref:System> 。 <xref:System.Environment.Exit%2A>需要您擁有 `UnmanagedCode` 許可權。 如果不這麼做， <xref:System.Security.SecurityException> 就會發生錯誤。  
  
 後面接著一個額外的關鍵字時， [end \<keyword> 語句](end-keyword-statement.md)會描寫適當程式或區塊定義的結尾。 例如，會 `End Function` 結束程式的定義 `Function` 。  
  
## <a name="example"></a>範例  
 下列範例 `End` 會使用語句來結束程式碼執行（如果使用者要求）。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援此陳述式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop 陳述式](stop-statement.md)
- [End \<keyword> 語句](end-keyword-statement.md)
