---
title: 使用設計工具變更 DataGridView 控制項中的資料行順序
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628744"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具變更 Windows Form DataGridView 控制項中資料行的順序

當您將 Windows Forms <xref:System.Windows.Forms.DataGridView> 控制項系結至資料來源時，自動產生之資料行的顯示順序會由資料來源決定。 如果這不是您偏好的順序，您可以使用設計工具來變更資料行的順序。 您可能也會想要將未系結的資料行加入至控制項，並變更其顯示順序。 如需如何以程式設計方式變更資料行順序的詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項中的資料行順序](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)。

下列程式需要具有包含 <xref:System.Windows.Forms.DataGridView> 控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

## <a name="to-change-the-column-order-using-the-designer"></a>若要使用設計工具變更資料行順序

1. 按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif)），然後選取 [**編輯資料行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 按一下 [選取的資料**行**] 清單右邊的向上或向下箭號，直到選取的資料行位於您想要的位置。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [操作說明：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
