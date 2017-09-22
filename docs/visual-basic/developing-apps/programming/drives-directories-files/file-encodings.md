---
title: "檔案編碼方式 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- character encodings
- files, encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6d4a12d3c6098271dad0a52a9c6799303b9fe81d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# File Encodings (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

檔案編碼方式 \(也稱為字元編碼方式\) 會指定在處理文字時字元的表示方式。  您可以根據編碼方式能否處理某些語言字元而決定偏好的編碼方式，不過，通常還是建議使用 Unicode。  
  
 讀取或寫入檔案時，對應不正確的檔案編碼方式可能會造成例外狀況 \(Exception\) 或錯誤的結果。  
  
## 編碼方式的類型  
 使用檔案時，建議使用 Unicode 編碼方式。  Unicode 是全球性的字元編碼標準，它會使用 16 位元字碼值表示現代電腦使用的所有字元，包含出版界的技術符號和特殊字元。  
  
 以前的字元編碼標準會包含傳統的字元集 \(Character Set\)，例如，使用 8 位元字碼值的 Windows ANSI 字元集，或是包含 8 位元值的組合，用以表示特定語言或地理區域所使用的字元。  
  
## <a name="encoding-class"></a>編碼類別  
 <xref:System.Text.Encoding> 類別表示字元編碼方式。 此表列出可用的編碼方式類型，並描述每個編碼方式。  
  
|||  
|-|-|  
|名稱|描述|  
|<xref:System.Text.ASCIIEncoding>|表示 Unicode 字元的 ASCII 字元編碼方式。|  
|<xref:System.Text.UnicodeEncoding>|表示 Unicode 字元的 UTF\-16 編碼方式。|  
|<xref:System.Text.UTF32Encoding>|表示 Unicode 字元的 UTF\-32 編碼方式。|  
|<xref:System.Text.UTF7Encoding>|表示 Unicode 字元的 UTF\-7 編碼方式。|  
|<xref:System.Text.UTF8Encoding>|表示 Unicode 字元的 UTF\-8 編碼方式。|  
  
## <a name="see-also"></a>另請參閱  
 [從檔案讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [寫入檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)

