---
title: 已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: c7a3e6bcd0db268a0e0acfc74c570e26f89cff6a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339069"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
不再支援單行陳述式。 檔案 I/O 功能可從`Microsoft.VisualBasic.FileSystem.LineInput`而且可以當做圖形功能`System.Drawing.Graphics.DrawLine`。  
  
 **錯誤 ID:** BC30830  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 如果執行檔案存取，使用`Microsoft.VisualBasic.FileSystem.LineInput`。  
  
2. 如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO>
- <xref:System.Drawing>
- [使用 Visual Basic 存取檔案](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
