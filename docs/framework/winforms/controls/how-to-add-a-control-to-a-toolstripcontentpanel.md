---
title: 如何：將控制項新增至 ToolStripContentPanel
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c9634e01c2c808a6134fbdf2b377050f225034d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-add-a-control-to-a-toolstripcontentpanel"></a>如何：將控制項新增至 ToolStripContentPanel
您可以程式設計方式將一個或多個控制項加入 <xref:System.Windows.Forms.ToolStripContentPanel>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何將 <xref:System.Windows.Forms.RichTextBox> 加入 <xref:System.Windows.Forms.ToolStripContentPanel>。  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要：  
  
-   System、System.Data 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))或 [ToolStripContainer 工作對話方塊](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [ToolStripContainer 控制項](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
