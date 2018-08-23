---
title: 使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 84ac57bf1bcf60664e2b18fed16a3bbe6c03dc68
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755004"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)
三種中央`My`提供使用功能的存取權對資訊和常用的物件`My.Application`(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>)， `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)，以及`My.User`(<xref:Microsoft.VisualBasic.ApplicationServices.User>)。 您可以使用這些物件分別存取與目前的應用程式、，安裝應用程式的電腦或目前使用者的應用程式時，相關的資訊。  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My.Application、 My.Computer 和 My.User  
 下列範例示範如何資訊可能會使用擷取`My`。  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 除了擷取資訊，透過這三個物件所公開的成員也可讓您執行該物件相關聯的方法。 比方說，您可以存取各種不同的方法來操作檔案，或更新透過登錄`My.Computer`。  
  
 檔案 I/O 大幅會更方便且更快速地`My`，其中包含各種不同的方法和屬性來操作檔案、 目錄和磁碟機。 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>物件可讓您讀取已分隔的大型結構化的檔案或固定寬度的欄位。 此範例會開啟`TextFieldParser``reader`並使用它來讀取`C:\TestFolder1\test1.txt`。  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application` 可讓您變更您的應用程式的文化特性。 下列範例會示範如何呼叫此方法。  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [My 如何相依於專案類型](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
