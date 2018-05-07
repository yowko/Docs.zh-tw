---
title: '&#39;行&#39;陳述式已不再支援 （Visual Basic 編譯器錯誤）'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 06bba0ebfc2faec24f4720c45de3bdcfec993499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;行&#39;陳述式已不再支援 （Visual Basic 編譯器錯誤）
不再支援單行陳述式。 檔案 I/O 功能可做為`Microsoft.VisualBasic.FileSystem.LineInput`和圖形功能是做為`System.Drawing.Graphics.DrawLine`。  
  
 **錯誤 ID:** BC30830  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  如果執行檔案存取，請使用`Microsoft.VisualBasic.FileSystem.LineInput`。  
  
2.  如果執行圖形，請使用`System.Drawing.Graphics.Drawline`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [使用 Visual Basic 存取檔案](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
