---
title: TableLayoutPanel 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: 65daba0ce1a6f1c37fb257c1029396577821aad9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009626"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel 控制項概觀
<xref:System.Windows.Forms.TableLayoutPanel> 控制項會在格線中排列其內容。 由於配置會在設計階段和執行階段執行，因此當應用程式環境變更時，配置也會隨著動態變更。 這可讓面板中的控制項按比例調整大小，以便回應變更 (例如，由於當地語系化所造成的父控制項調整大小或文字長度變更)。  
  
 任何 Windows Form 控制項都可以是 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的子系，包括 <xref:System.Windows.Forms.TableLayoutPanel> 的其他執行個體。 這可讓您建構在執行階段適應變更的複雜配置。  
  
 根據 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>、<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 屬性的值，<xref:System.Windows.Forms.TableLayoutPanel> 控制項可以展開，以在新控制項加入時加以容納。 將 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> 或 <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 屬性設定為值 0，可指定對應方向的 <xref:System.Windows.Forms.TableLayoutPanel> 將解除繫結。  
  
 您也可以在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項已完全充滿子控制項之後，控制展開的方向 (水平或垂直)。 <xref:System.Windows.Forms.TableLayoutPanel> 控制項預設會向下加入資料列來展開。  
  
 如果您希望資料列和資料行的行為不同於預設的行為，就可以使用 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 屬性來控制資料列和資料行的屬性。 您可以個別設定資料列或資料行的屬性。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項會將下列屬性加入其子控制項：`Cell`、`Column`、`Row`、`ColumnSpan` 和 `RowSpan`。  
  
 您可以設定子控制項的 `ColumnSpan` 或 `RowSpan` 屬性，來合併 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的儲存格。  
  
1. [如何：對齊和縮放 TableLayoutPanel 控制項中的控制項](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [如何：合併資料列和 TableLayoutPanel 控制項中的資料行](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3. [如何：編輯資料行和 TableLayoutPanel 控制項中的資料列](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4. [逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [如何：設計可適當回應當地語系化的 Windows Forms 配置](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [如何：建立適用於資料輸入且可調整大小的 Windows Form](how-to-create-a-resizable-windows-form-for-data-entry.md)
- [TableLayoutPanel 控制項的最佳作法](best-practices-for-the-tablelayoutpanel-control.md)
