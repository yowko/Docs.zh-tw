---
title: 已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 4ca1538dbde0d585b7b421d60cde4531c00e9145
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873840"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)

不再支援行語句。 檔案 i/o 功能可供使用 `Microsoft.VisualBasic.FileSystem.LineInput` ，而且圖形功能也可供使用 `System.Drawing.Graphics.DrawLine` 。  
  
 **錯誤識別碼：** BC30830  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 如果執行檔案存取，請使用 `Microsoft.VisualBasic.FileSystem.LineInput` 。  
  
2. 如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO>
- <xref:System.Drawing>
- [使用 Visual Basic 存取檔案](../../developing-apps/programming/drives-directories-files/file-access.md)
