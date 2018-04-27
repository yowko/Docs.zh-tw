---
title: 如何：聯結 ToolStripPanels
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
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 80a3194b4c300bf72306abd3f080fbff9eca6e52
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-join-toolstrippanels"></a>如何：聯結 ToolStripPanels
您可以在執行階段將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>，以提供多重文件介面 (MDI) 應用程式的彈性。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何將 <xref:System.Windows.Forms.ToolStrip> 控制項加入 <xref:System.Windows.Forms.ToolStripPanel>。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 建置此範例從 visual Basic 或 Visual C# 命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [操作說明：針對 MDI 使用 ToolStripPanels](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)
