---
title: 作法：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: f47eb29bf9ae077555f352d10c667bac4ade9373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968327"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>作法：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列
有時候您會想要防止使用者在您的 <xref:System.Windows.Forms.DataGridView> 控制項中輸入新的資料列或刪除現有的資料列。 新的資料列會在控制項底部的新記錄的特殊資料列中輸入。 當您停用資料列加入時, 不會顯示新記錄的資料列。 接著, 您可以停用資料列刪除和儲存格編輯, 讓控制項成為完全唯讀的。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

## <a name="to-prevent-row-addition-and-deletion"></a>防止加入和刪除資料列

- 按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後清除 [**啟用加入**] 和 [**啟用刪除**] 核取方塊。

    > [!NOTE]
    > 若要將控制項設為完全唯讀, 請清除 [**啟用編輯**] 核取方塊。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
