---
title: HOW TO：將控制項新增至索引標籤頁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: b42845ab996c0985fe6a48ac588e6d706905faac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195848"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>HOW TO：將控制項新增至索引標籤頁
您可以使用 Windows Form<xref:System.Windows.Forms.TabControl>以顯示其他控制項，以組織方式。 下列程序示範如何將按鈕加入到第一個索引標籤。如需將圖示新增至索引標籤頁的標籤部分資訊，請參閱[How to:變更 Windows Form TabControl 的外觀](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)。  
  
### <a name="to-add-a-control-programmatically"></a>若要以程式設計方式加入控制項  
  
1.  使用<xref:System.Windows.Forms.Control.ControlCollection.Add%2A>方法所傳回的集合<xref:System.Windows.Forms.Control.Controls%2A>屬性<xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [TabControl 控制項](tabcontrol-control-windows-forms.md)
- [TabControl 控制項概觀](tabcontrol-control-overview-windows-forms.md)
- [HOW TO：變更 Windows Forms TabControl 的外觀](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [HOW TO：停用索引標籤頁](how-to-disable-tab-pages.md)
- [HOW TO：使用 Windows Forms TabControl 新增和移除索引標籤](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
