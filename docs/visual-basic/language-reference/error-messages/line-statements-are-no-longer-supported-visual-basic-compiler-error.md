---
title: 已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: a3d243f39f3fc45ca6b1ba0d26892d4c3db56f59
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397294"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
已不再支援行語句。 檔案 i/o 功能可供使用 `Microsoft.VisualBasic.FileSystem.LineInput` ，而且圖形功能可作為提供 `System.Drawing.Graphics.DrawLine` 。  
  
 **錯誤識別碼：** BC30830  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 如果要執行檔案存取，請使用 `Microsoft.VisualBasic.FileSystem.LineInput` 。  
  
2. 如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO>
- <xref:System.Drawing>
- [使用 Visual Basic 存取檔案](../../developing-apps/programming/drives-directories-files/file-access.md)
