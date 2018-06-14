---
title: 檔案編碼方式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 30aba517b3b0fbb5fa5bea48134934b2c2d26e50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582281"
---
# <a name="file-encodings-visual-basic"></a>檔案編碼方式 (Visual Basic)
檔案編碼方式，也稱為字元編碼方式，指定在處理文字時如何代表字元。 就可以或無法處理的語言字元部分而言，可能會偏好使用某種編碼，但是通常偏好使用 Unicode。  
  
 讀取或寫入檔案時，不相符的檔案編碼方式可能會導致例外狀況或不正確的結果。  
  
## <a name="types-of-encodings"></a>編碼方式的類型  
 使用檔案時，Unicode 是慣用的編碼方式。 Unicode 是全球字元編碼標準，可使用 16 位元字碼值代表現代計算中所使用的所有字元 (包括發行中所使用的技術符號和特殊字元)。  
  
 先前的字元編碼標準包含傳統字元集 (例如使用 8 位元字碼值或 8 位元值組合的 Windows ANSI 字元集)，以代表特定語言或地區中所使用的字元。  
  
## <a name="encoding-class"></a>編碼類別  
 <xref:System.Text.Encoding> 類別表示字元編碼方式。 此表列出可用的編碼方式類型，並描述每個編碼方式。  
  
|名稱|描述|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|代表 Unicode 字元的 ASCII 字元編碼方式。|  
|<xref:System.Text.UnicodeEncoding>|代表 Unicode 字元的 UTF-16 編碼方式。|  
|<xref:System.Text.UTF32Encoding>|代表 Unicode 字元的 UTF-32 編碼方式。|  
|<xref:System.Text.UTF7Encoding>|代表 Unicode 字元的 UTF-7 編碼方式。|  
|<xref:System.Text.UTF8Encoding>|代表 Unicode 字元的 UTF-8 編碼方式。|  
  
## <a name="see-also"></a>請參閱  
 [從檔案讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [寫入檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
