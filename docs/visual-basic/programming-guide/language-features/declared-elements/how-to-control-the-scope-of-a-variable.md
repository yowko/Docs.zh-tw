---
title: 如何：控制變數的範圍
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 2ce7c1700eec54542719e6e0880466ca136e86f6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095429"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>如何：控制變數的範圍 (Visual Basic)

一般情況下，變數會在您宣告的區域中，于 *範圍*內或可供參考。 在某些情況下，變數的 *存取層級* 可能會影響其範圍。  
  
 如需詳細資訊，請參閱 [Scope in Visual Basic](scope.md)。  
  
## <a name="scope-at-block-or-procedure-level"></a>區塊或程式層級的範圍  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>讓變數只在區塊內可見  
  
- 在該區塊的起始和終止宣告語句之間放置變數的 [Dim 語句](../../../language-reference/statements/dim-statement.md) ，例如在 `For` 迴圈的和語句之間 `Next` `For` 。  
  
     您只能從區塊內參考該變數。  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>讓變數只在程式中顯示  
  
- 將變數的語句放在程式 `Dim` 內，但在任何區塊 (（例如 `With` ... `End With` block) ）之外。  
  
     您只能從程式內（包括程式中包含的任何區塊內）參考該變數。  
  
## <a name="scope-at-module-or-namespace-level"></a>模組或命名空間層級的範圍  

 為了方便起見，單一詞彙 *模組層級* 同樣適用于模組、類別和結構。 模組層級變數的存取層級會決定其範圍。 包含模組、類別或結構的命名空間也會影響範圍。  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>讓變數在整個模組、類別或結構中都可見  
  
1. 將變數的語句放在 `Dim` 模組、類別或結構內，但在任何程式之外。  
  
2. 在語句中包含 [私](../../../language-reference/modifiers/private.md) 用關鍵字 `Dim` 。  
  
3. 您可以從模組、類別或結構內的任何位置參考變數，但不能從外部參考該變數。  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>讓變數在命名空間中可見  
  
1. 將變數的語句放在 `Dim` 模組、類別或結構內，但在任何程式之外。  
  
2. 在語句中包含 [Friend](../../../language-reference/modifiers/friend.md) 或 [Public](../../../language-reference/modifiers/public.md) 關鍵字 `Dim` 。  
  
3. 您可以從包含模組、類別或結構的命名空間中的任何位置參考變數。  
  
## <a name="example"></a>範例  

 下列範例會在模組層級宣告變數，並限制其在模組內的程式碼可見度。  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 在上述範例中，模組中定義的所有程式都 `demonstrateScope` 可以參考 `String` 變數 `strMsg` 。 `usePrivateVariable`呼叫程式時，它會在對話方塊中顯示字串變數的內容 `strMsg` 。  
  
 使用上述範例中的下列變更，可以在其宣告的 `strMsg` 命名空間中的任何位置，將字串變數參考至程式碼。  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>穩固程式設計  

 變數的範圍愈窄，您所擁有的機會不會被用來取代另一個具有相同名稱的變數。 您也可以將參考比對的問題降至最低。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  

 變數的範圍愈窄，惡意程式碼可能不當使用它的機率就愈小。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的範圍](scope.md)
- [Visual Basic 中的存留期](lifetime.md)
- [Visual Basic 中的存取層級](access-levels.md)
- [變數](../variables/index.md)
- [變數宣告](../variables/variable-declaration.md)
- [Dim 陳述式](../../../language-reference/statements/dim-statement.md)
