---
title: 如何：叫用委派方法
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 520bacfbe6103490e0459cd5af149c1d55a8fce4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345257"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>如何：叫用委派方法 (Visual Basic)

這個範例示範如何將方法與委派產生關聯，然後透過委派叫用該方法。

### <a name="create-the-delegate-and-matching-procedures"></a>建立委派和比對程式

1. 建立名為 `MySubDelegate`的委派。

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. 宣告一個類別，其中包含具有與委派相同簽章的方法。

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. 定義方法來建立委派的實例，並藉由呼叫內建的 `Invoke` 方法，叫用與委派相關聯的方法。

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a>請參閱

- [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [多執行緒應用程式](../../../../standard/threading/using-threads-and-threading.md)
