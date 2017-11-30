---
title: "如何：繼承 Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e986c79887ad19c77761b5ce134e4a3d68200d1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inherit-windows-forms"></a>如何：繼承 Windows Form
藉由繼承自基底表單建立新的 Windows Form，可以很快地複製您的最佳成果，而無須在每次需要它時都要完成重建表單的程序。  
  
 如需在設計階段使用 [繼承選取器] 對話方塊繼承表單的詳細資訊，以及如何以視覺化方式區分繼承控制項的安全性層級，請參閱[如何：使用繼承選取器對話方塊繼承表單](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)。  
  
 **附註：**為了繼承自表單，包含該表單的檔案或命名空間必須已建置為可執行檔或 DLL。 若要建置專案，請從 [建置] 功能表中選擇 [建置]。 此外，命名空間的參考也必須加入至繼承表單的類別。 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-inherit-a-form-programmatically"></a>以程式設計方式繼承表單  
  
1.  在類別中，加入對包含您想要繼承之表單的命名空間的參考。  
  
2.  在類別定義中，加入要繼承之表單的參考。 參考必須包括包含表單的命名空間，後面接著句點，然後是基底表單本身的名稱。  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 繼承表單時，請記住，呼叫兩次事件處理常式可能會發生問題，因為每個事件都會由基底類別和繼承的類別處理。 如需如何避免這個問題的詳細資訊，請參閱[針對 Visual Basic 中的繼承事件處理常式進行疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Inherits 陳述式](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [Imports 陳述式 (.NET 命名空間和類型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [修改基底表單外觀的效果](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Windows Forms 視覺繼承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
