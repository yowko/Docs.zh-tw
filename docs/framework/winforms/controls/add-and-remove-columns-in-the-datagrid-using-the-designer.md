---
title: "如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fdb57cf2134ee4f221a26db61cfdcc48dc92548
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行
Windows Form<xref:System.Windows.Forms.DataGridView>控制項必須包含資料行，才能顯示資料。 如果您計劃手動填入控制項，您必須自己加入資料行。 或者，您可以將控制項繫結至資料來源，這會產生並自動填入資料行。 如果資料來源包含多個資料行，比您想要顯示，您可以移除不必要的資料行。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-add-a-column-using-the-designer"></a>若要加入資料行使用設計工具  
  
1.  按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**加入資料行**。  
  
2.  在**加入資料行**對話方塊方塊中，選擇**資料繫結資料行**選項並選取資料行從資料來源，或選擇**繫結資料行**選項，然後將資料行定義使用提供的欄位。  
  
3.  按一下**新增**按鈕來加入資料行，使其出現在設計工具中的現有資料行未已填滿控制項顯示區域。  
  
    > [!NOTE]
    >  您可以修改資料行屬性**編輯資料行**對話方塊中，您可以從控制項的智慧標籤來存取。  
  
### <a name="to-remove-a-column-using-the-designer"></a>若要移除的使用設計工具的資料行  
  
1.  選擇**編輯資料行**從控制項的智慧標籤。  
  
2.  選取的資料行**選取的資料行**清單。  
  
3.  按一下**移除**按鈕來刪除資料行，就會從設計工具中消失。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 [如何： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
