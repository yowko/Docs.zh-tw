---
title: HOW TO：在 Windows Form ListView 控制項中選取的項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: ed3e68fbe77f194ed04d15f99a48657a32a13b50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644712"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>HOW TO：在 Windows Form ListView 控制項中選取的項目
此範例示範如何以程式設計方式在 Windows Form 中選取的項目<xref:System.Windows.Forms.ListView>控制項。 以程式設計方式選取項目不會自動變更焦點<xref:System.Windows.Forms.ListView>控制項。 基於這個理由，您通常也要設定項目，如已取得焦點時選取項目。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   A<xref:System.Windows.Forms.ListView>控制項，名為`listView1`包含至少一個項目。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
