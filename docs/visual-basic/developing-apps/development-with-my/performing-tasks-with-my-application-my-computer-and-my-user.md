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
ms.openlocfilehash: fc9fd9093a3db4785bfc94719dbae9ec1d586050
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329584"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)

提供資訊和常用功能存取權的三個中央 `My` 物件是 `My.Application` （<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>）、`My.Computer` （<xref:Microsoft.VisualBasic.Devices.Computer>）和 `My.User` （<xref:Microsoft.VisualBasic.ApplicationServices.User>）。 您可以使用這些物件來存取與目前應用程式、應用程式安裝所在的電腦，或是應用程式目前的使用者相關的資訊。  
  
## <a name="myapplication-mycomputer-and-myuser"></a>我的應用程式、我的電腦和我的使用者。  

 下列範例示範如何使用 `My`來抓取資訊。  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 除了抓取資訊之外，透過這三個物件公開的成員也可讓您執行與該物件相關的方法。 例如，您可以存取各種不同的方法來操作檔案，或透過 `My.Computer`更新登錄。  
  
 使用 `My`，檔案 i/o 會大幅簡化且更快速，其中包括用來管理檔案、目錄和磁片磁碟機的各種方法和屬性。 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件可讓您從具有分隔或固定寬度欄位的大型結構化檔案中讀取。 這個範例會開啟 `TextFieldParser` `reader`，並使用它從 `C:\TestFolder1\test1.txt`讀取。  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application` 可讓您變更應用程式的文化特性。 下列範例會示範如何呼叫這個方法。  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My 如何相依於專案類型](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
