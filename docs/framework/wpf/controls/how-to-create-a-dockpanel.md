---
title: HOW TO：建立 DockPanel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], creating
ms.assetid: 9194f663-e279-4f1a-86d7-125a57d05c6f
ms.openlocfilehash: 35434a13386ae89fdc1428bd632d21c1551c9871
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911116"
---
# <a name="how-to-create-a-dockpanel"></a><span data-ttu-id="767a6-102">HOW TO：建立 DockPanel</span><span class="sxs-lookup"><span data-stu-id="767a6-102">How to: Create a DockPanel</span></span>
## <a name="example"></a><span data-ttu-id="767a6-103">範例</span><span class="sxs-lookup"><span data-stu-id="767a6-103">Example</span></span>  
 <span data-ttu-id="767a6-104">下列範例會建立和使用的執行個體<xref:System.Windows.Controls.DockPanel>使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="767a6-104">The following example creates and uses an instance of <xref:System.Windows.Controls.DockPanel> by using code.</span></span> <span data-ttu-id="767a6-105">此範例會示範如何藉由建立五個分割空間<xref:System.Windows.Shapes.Rectangle>項目和定位 （固定） 其父代內<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="767a6-105">The example shows you how to partition space by creating five <xref:System.Windows.Shapes.Rectangle> elements and positioning (docking) them inside a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="767a6-106">如果您保留預設設定，最終的矩形所填滿所有剩餘的未配置的空間。</span><span class="sxs-lookup"><span data-stu-id="767a6-106">If you retain the default setting, the final rectangle fills all the remaining unallocated space.</span></span>  
  
 [!code-csharp[DockPanelCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelCode/CSharp/DockPanel_Code.cs#1)]
 [!code-vb[DockPanelCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelCode/VisualBasic/dockpanel_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="767a6-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="767a6-107">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Dock>
- [<span data-ttu-id="767a6-108">面板概觀</span><span class="sxs-lookup"><span data-stu-id="767a6-108">Panels Overview</span></span>](panels-overview.md)
