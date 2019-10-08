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
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005287"
---
# <a name="-quiet"></a>-quiet

防止編譯器顯示語法相關錯誤和警告的程式碼。

## <a name="syntax"></a>語法

```console
-quiet
```

## <a name="remarks"></a>備註

`-quiet` 預設為非作用中。 當編譯器報告語法相關的錯誤或警告時，它也會從原始程式碼輸出這一行。 對於剖析編譯器輸出的應用程式而言，編譯器可能更方便只輸出診斷的文字。

在下列範例中，`Module1` 會在編譯時輸出包含原始程式碼的錯誤，而不 `-quiet`。

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

以 `-quiet` 編譯，編譯器只會輸出下列內容：

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。

## <a name="example"></a>範例

下列程式碼會編譯 `T2.vb`，而且不會顯示語法相關編譯器診斷的程式碼：

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
