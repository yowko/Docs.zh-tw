---
title: '&#39;行&#39;陳述式已不再支援 （Visual Basic 編譯器錯誤）'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 36226cc371ffb8a51cb8d0f918952f1c717aea10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702964"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;行&#39;陳述式已不再支援 （Visual Basic 編譯器錯誤）
不再支援單行陳述式。 檔案 I/O 功能可從`Microsoft.VisualBasic.FileSystem.LineInput`而且可以當做圖形功能`System.Drawing.Graphics.DrawLine`。  
  
 **錯誤 ID:** BC30830  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  如果執行檔案存取，使用`Microsoft.VisualBasic.FileSystem.LineInput`。  
  
2.  如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.IO>
- <xref:System.Drawing>
- [使用 Visual Basic 存取檔案](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
