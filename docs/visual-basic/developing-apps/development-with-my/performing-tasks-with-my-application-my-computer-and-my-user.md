---
title: 使用 My.Application、My.Computer 及 My.User 執行工作
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 55961d6857b690fc2726f541df8a5497a3207928
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411690"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)

`My`提供資訊和常用功能存取權的三個中央物件為 `My.Application` （ <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> ）、 `My.Computer` （ <xref:Microsoft.VisualBasic.Devices.Computer> ）和 `My.User` （ <xref:Microsoft.VisualBasic.ApplicationServices.User> ）。 您可以使用這些物件來存取與目前應用程式、應用程式安裝所在的電腦，或是應用程式目前的使用者相關的資訊。  
  
## <a name="myapplication-mycomputer-and-myuser"></a>我的應用程式、我的電腦和我的使用者。  

 下列範例示範如何使用來取出資訊 `My` 。  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 除了抓取資訊之外，透過這三個物件公開的成員也可讓您執行與該物件相關的方法。 例如，您可以存取各種不同的方法來操作檔案，或透過更新登錄 `My.Computer` 。  
  
 檔案 i/o 使用的方式明顯更輕鬆且更快速 `My` ，其中包括用來管理檔案、目錄和磁片磁碟機的各種方法和屬性。 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>物件可讓您從具有分隔或固定寬度欄位的大型結構化檔案中讀取。 這個範例會開啟 `TextFieldParser` `reader` ，並使用它來讀取 `C:\TestFolder1\test1.txt` 。  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application`可讓您變更應用程式的文化特性。 下列範例會示範如何呼叫這個方法。  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My 與專案類型的相依關係](how-my-depends-on-project-type.md)
