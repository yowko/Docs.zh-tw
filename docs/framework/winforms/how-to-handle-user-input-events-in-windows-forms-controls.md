---
title: HOW TO：處理 Windows Form 控制項中的使用者輸入的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 886558eb33ffbbec65917f15f4da16673518dce9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723948"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>HOW TO：處理 Windows Form 控制項中的使用者輸入的事件
此範例示範如何處理 Windows Form 控制項中可能發生的大部分鍵盤、滑鼠、焦點和驗證事件。 名為 `TextBoxInput` 的文字方塊中有焦點時，會接收那些事件，而每個事件的相關資訊，會依據事件引發的順序，寫入名為 `TextBoxOutput` 的文字方塊中。 應用程式中也包含一組核取方塊，可用來篩選所要報告的事件。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱
- [Windows Forms 中的使用者輸入](user-input-in-windows-forms.md)
