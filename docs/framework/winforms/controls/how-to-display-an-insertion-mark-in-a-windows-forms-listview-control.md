---
title: 如何：在 Windows Forms ListView 控制項中顯示插入標記
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
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03c2667225aa3161b6325909cc54c46e55a39b74
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>如何：在 Windows Forms ListView 控制項中顯示插入標記
<xref:System.Windows.Forms.ListView> 控制項中的插入標記會向使用者顯示將會插入拖曳項目的點。 當使用者將項目拖曳至另外兩個項目之間的某個點時，插入標記會顯示該項目的預期新位置。  
  
> [!NOTE]
>  當您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時，只有 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上會出現插入標記功能。 在舊版作業系統上，與插入標記相關的任何程式碼都沒有任何作用，而且不會出現插入標記。 如需詳細資訊，請參閱<xref:System.Windows.Forms.ListViewInsertionMark>。  
  
 下圖顯示插入標記：  
  
 ![ListView 插入標記](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")  
  
 下列程式碼範例示範如何使用這項功能。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewInsertionMark>  
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP 功能和 Windows Forms 控制項](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [逐步解說：在 Windows Forms 中執行拖放作業](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
