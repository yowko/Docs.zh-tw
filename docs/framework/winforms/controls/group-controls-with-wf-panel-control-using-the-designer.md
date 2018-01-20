---
title: "如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1c6dd45d2070c77b34c66388b397bb784215654
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項
Windows Form<xref:System.Windows.Forms.Panel>控制項可用來將其他控制項組成群組。 有群組控制項的三個原因。 其中一個是視覺化群組相關的表單項目，清楚的使用者介面。另一個是以程式設計方式分組，選項按鈕： 例如，上次是在設計階段將控制項移做為一個單位。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-create-a-group-of-controls"></a>若要建立的控制項群組  
  
1.  拖曳<xref:System.Windows.Forms.Panel>控制項從**Windows Form**  索引標籤的 工具箱 拖曳至表單。  
  
2.  將其他控制項加入面板中，每個面板內繪製。  
  
     如果您有想要住在面板中的現有控制項，您可以選取所有控制項，剪下到剪貼簿中，都選取並<xref:System.Windows.Forms.Panel>控制項，然後再將它們貼至 [面板]。 您也可以將它們拖曳到 [面板]。  
  
3.  （選擇性）如果您想要將框線加入至面板，設定其<xref:System.Windows.Forms.BorderStyle>屬性。 有三個選擇： <xref:System.Windows.Forms.BorderStyle.Fixed3D>， <xref:System.Windows.Forms.BorderStyle.FixedSingle>，和<xref:System.Windows.Forms.BorderStyle.None>。  
  
## <a name="see-also"></a>請參閱  
 [Panel 控制項](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [操作說明：設定面板背景](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
