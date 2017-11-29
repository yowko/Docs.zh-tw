---
title: "如何：將控制項加入至索引標籤頁"
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
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ac6e436aeeafcaa66ff0e3bec213c2316302fd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>如何：將控制項加入至索引標籤頁
您可以使用 Windows Form<xref:System.Windows.Forms.TabControl>以顯示其他控制項，以組織方式。 下列程序示範如何將按鈕加入到第一個索引標籤。如需將圖示加入至索引標籤頁的標籤部分資訊，請參閱[如何： 變更 Windows Form TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)。  
  
### <a name="to-add-a-control-programmatically"></a>若要以程式設計方式加入控制項  
  
1.  使用<xref:System.Windows.Forms.Control.ControlCollection.Add%2A>方法所傳回的集合<xref:System.Windows.Forms.Control.Controls%2A>屬性<xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [TabControl 控制項](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [操作說明：變更 Windows Forms TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [操作說明：停用索引標籤頁](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [操作說明：使用 Windows Forms TabControl 加入和移除索引標籤](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
