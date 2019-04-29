---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788839"
---
# <a name="-quiet"></a>-quiet

防止編譯器顯示語法相關錯誤和警告的程式碼。

## <a name="syntax"></a>語法

```
-quiet
```

## <a name="remarks"></a>備註

`-quiet` 預設為非作用中。 當編譯器報告語法相關錯誤或警告時，它也會輸出從來源程式碼行。 剖析編譯器輸出的應用程式，它可能會更方便的編譯器輸出的診斷文字項目。

在下列範例中，`Module1`輸出錯誤包含原始程式碼，而不需要編譯時`-quiet`。

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

輸出：

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

以編譯`-quiet`，編譯器只會輸出下列：

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> `-quiet`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。

## <a name="example"></a>範例

下列程式碼編譯`T2.vb`並不會顯示語法相關的編譯器診斷的程式碼：

```
vbc -quiet t2.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
