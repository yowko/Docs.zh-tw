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
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="f7693-102">作法：擴展 TableLayoutPanel 控制項中的資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="f7693-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="f7693-103">控制項中的<xref:System.Windows.Forms.TableLayoutPanel>控制項可以跨越連續的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="f7693-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>

## <a name="to-span-columns-and-rows"></a><span data-ttu-id="f7693-104">跨資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="f7693-104">To span columns and rows</span></span>

1. <span data-ttu-id="f7693-105">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f7693-105">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="f7693-106">將控制項從 [**工具箱**] 拖曳至<xref:System.Windows.Forms.TableLayoutPanel>控制項的左上角儲存格。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="f7693-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="f7693-107">將控制項的 ColumnSpan 屬性設定為**2**。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="f7693-107">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="f7693-108">請注意, <xref:System.Windows.Forms.Button>控制項會跨越第一個和第二個數據行。</span><span class="sxs-lookup"><span data-stu-id="f7693-108">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>

4. <span data-ttu-id="f7693-109">將控制項的 RowSpan 屬性設定為**2**。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="f7693-109">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="f7693-110">請注意, <xref:System.Windows.Forms.Button>控制項會跨越第一個和第二個數據列。</span><span class="sxs-lookup"><span data-stu-id="f7693-110">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>

5. <span data-ttu-id="f7693-111">將控制項的 ColumnSpan 屬性設定為**1**。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="f7693-111">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="f7693-112">請注意, <xref:System.Windows.Forms.Button>控制項會移到第一個資料行, 並跨越第一個和第二個數據列。</span><span class="sxs-lookup"><span data-stu-id="f7693-112">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7693-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7693-113">See also</span></span>

- [<span data-ttu-id="f7693-114">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="f7693-114">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
