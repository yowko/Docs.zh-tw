---
title: 作法：擴展 TableLayoutPanel 控制項中的資料列和資料行
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039692"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>作法：擴展 TableLayoutPanel 控制項中的資料列和資料行
控制項中的<xref:System.Windows.Forms.TableLayoutPanel>控制項可以跨越連續的資料列和資料行。

## <a name="to-span-columns-and-rows"></a>跨資料行和資料列

1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。

2. 將控制項從 [**工具箱**] 拖曳至<xref:System.Windows.Forms.TableLayoutPanel>控制項的左上角儲存格。 <xref:System.Windows.Forms.Button>

3. 將控制項的 ColumnSpan 屬性設定為**2**。 <xref:System.Windows.Forms.Button> 請注意, <xref:System.Windows.Forms.Button>控制項會跨越第一個和第二個數據行。

4. 將控制項的 RowSpan 屬性設定為**2**。 <xref:System.Windows.Forms.Button> 請注意, <xref:System.Windows.Forms.Button>控制項會跨越第一個和第二個數據列。

5. 將控制項的 ColumnSpan 屬性設定為**1**。 <xref:System.Windows.Forms.Button> 請注意, <xref:System.Windows.Forms.Button>控制項會移到第一個資料行, 並跨越第一個和第二個數據列。

## <a name="see-also"></a>另請參閱

- [TableLayoutPanel 控制項](tablelayoutpanel-control-windows-forms.md)
