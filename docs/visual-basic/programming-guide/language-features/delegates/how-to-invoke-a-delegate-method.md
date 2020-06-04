---
title: 如何：叫用委派方法
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: f319727c007b93c7b334af0598f1b9f7c034144d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410717"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>如何：叫用委派方法 (Visual Basic)

這個範例示範如何將方法與委派產生關聯，然後透過委派叫用該方法。

### <a name="create-the-delegate-and-matching-procedures"></a>建立委派和比對程式

1. 建立名為的委派 `MySubDelegate` 。

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

3. 定義方法，以建立委派的實例，並藉由呼叫內建方法來叫用與委派相關聯的方法 `Invoke` 。

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a>另請參閱

- [Delegate 陳述式](../../../language-reference/statements/delegate-statement.md)
- [委派](index.md)
- [事件](../events/index.md)
- [多執行緒應用程式](../../../../standard/threading/using-threads-and-threading.md)
