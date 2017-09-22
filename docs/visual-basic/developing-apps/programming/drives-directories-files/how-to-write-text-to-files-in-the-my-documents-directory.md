---
title: "如何：在 Visual Basic 中將文字寫入我的文件目錄中的檔案"
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
- files, writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files, in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: 19
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
ms.openlocfilehash: c900072d184469ead75bb76a3e152edce357a34f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# How to: Write Text to Files in the My Documents Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`My.Computer.FileSystem.SpecialDirectories` 物件可以讓您存取特殊的目錄，例如 \[**MyDocuments**\] 目錄。  
  
## 程序  
  
#### 若要在我的文件目錄中撰寫新的文字檔  
  
1.  使用 `My.Computer.FileSystem.SpecialDirectories.MyDocuments` 屬性 \(Property\) 提供路徑。  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  使用 `WriteAllText` 方法，將文字寫入指定的檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## 範例  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## 編譯程式碼  
 將 `test.txt` 換成您要寫入之檔案的名稱。  
  
## 穩固程式設計  
 此程式碼會重新擲回可能在將文字寫入檔案時發生的所有例外狀況。  若要減少類似的例外狀況，可以使用 Windows Form 控制項 \(例如，能將使用者選項限制為有效檔名的 [OpenFileDialog](../Topic/OpenFileDialog%20Component%20\(Windows%20Forms\).md) 和 [SaveFileDialog](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md) 元件\)。  不過，使用這些控制項並不容易。  因為在使用者選擇檔案到程式碼執行的這段時間，檔案系統有可能變更。  因此在使用檔案時，幾乎一定要有例外狀況處理 \(Exception Handling\)。  
  
## .NET Framework 安全性  
 如果是在部分信任的內容中執行，則程式碼可能會因權限不足而擲回例外狀況。  如需詳細資訊，請參閱[Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)。  
  
 此範例會建立新檔案。  如果應用程式需要建立檔案，它將需要資料夾的建立使用權限。  使用權限是使用存取控制清單設定的。  如果檔案已存在，應用程式只需要寫入使用權限，也就是較少的使用權限。  可能的話，在部署期間建立檔案，且只授與讀取單一檔案的使用權限 \(而不是授與建立資料夾的使用權限\)，這樣做會比較安全。  此外，較安全的做法是將資料寫入使用者資料夾，而不要寫入根資料夾或 \[**Program Files**\] 資料夾。  如需詳細資訊，請參閱 [ACL Technology Overview](http://msdn.microsoft.com/zh-tw/06fbf66d-6f02-4378-b863-b2f12e349045)。  
  
## 請參閱  
 <xref:System.IO.Path.Combine%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>

