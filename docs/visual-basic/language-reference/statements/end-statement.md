---
title: End 陳述式 (Visual Basic)
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
ms.openlocfilehash: 4fc4fd36fb6b057195e9d8a79eb0a5b3ac9ff95c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638138"
---
# <a name="end-statement"></a>End 陳述式
立即結束執行。  
  
## <a name="syntax"></a>語法  
  
```  
End  
```  
  
## <a name="remarks"></a>備註  
 您可以將`End`強制整個應用程式停止執行程序中的任何位置的陳述式。 `End` 關閉任何開啟的檔案`Open`陳述式，並清除所有應用程式的變數。 只要不有任何其他程式會儲存其物件的參考，並沒有其程式碼正在關閉應用程式。  
  
> [!NOTE]
>  `End`陳述式會突然，停止執行程式碼，並不會呼叫`Dispose`或`Finalize`方法或任何其他 Visual Basic 程式碼。 其他程式所持有的物件參考都會失效。 如果`End`陳述式中遇到`Try`或是`Catch`區塊中，控制項不會通過對應`Finally`區塊。  
  
 `Stop`陳述式暫停執行，但不同於`End`，不會關閉任何檔案或清除任何變數，但若發生在已編譯可執行檔 (.exe) 檔案中。  
  
 因為`End`會終止您的應用程式不會理會可能已經開啟的任何資源，您應該試著關閉完全後才能使用它。 比方說，如果您的應用程式有任何開啟的表單，您應該先關閉這些控制項達到`End`陳述式。  
  
 您應該使用`End`盡量節制，而且只有當您需要立即停止。 終止程序的一般方式 ([Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)並[Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)) 不僅完全關閉程序，但也可讓呼叫端程式碼完全關閉。 主控台應用程式，比方說，只要`Return`從`Main`程序。  
  
> [!IMPORTANT]
>  `End`陳述式會呼叫<xref:System.Environment.Exit%2A>方法<xref:System.Environment>類別在<xref:System>命名空間。 <xref:System.Environment.Exit%2A> 您必須有`UnmanagedCode`權限。 如果您未這麼做，<xref:System.Security.SecurityException>就會發生錯誤。  
  
 其他的關鍵字，後面跟著[結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)描述定義適當的程序或區塊的結尾。 例如，`End Function`結束的定義`Function`程序。  
  
## <a name="example"></a>範例  
 下列範例會使用`End`陳述式來終止執行程式碼，如果在使用者要求。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援此陳述式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop 陳述式](../../../visual-basic/language-reference/statements/stop-statement.md)
- [結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
