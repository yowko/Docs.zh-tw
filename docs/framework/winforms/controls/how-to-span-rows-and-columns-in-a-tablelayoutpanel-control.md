---
title: "如何：擴展 TableLayoutPanel 控制項中的資料列和資料行"
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
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24b281e6e1ab56e2c7387435bf2429e7e107c4b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="8beee-102">如何：擴展 TableLayoutPanel 控制項中的資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="8beee-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="8beee-103">中的控制項<xref:System.Windows.Forms.TableLayoutPanel>控制項可以跨越相鄰的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="8beee-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8beee-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="8beee-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8beee-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="8beee-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8beee-106">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="8beee-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="8beee-107">若要擴展資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="8beee-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="8beee-108">拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="8beee-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="8beee-109">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**左上方儲存格的<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="8beee-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="8beee-110">設定<xref:System.Windows.Forms.Button>控制項的**ColumnSpan**屬性**2**。</span><span class="sxs-lookup"><span data-stu-id="8beee-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="8beee-111">請注意，<xref:System.Windows.Forms.Button>控制項跨越的第一個和第二個資料行。</span><span class="sxs-lookup"><span data-stu-id="8beee-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="8beee-112">設定<xref:System.Windows.Forms.Button>控制項的**RowSpan**屬性**2**。</span><span class="sxs-lookup"><span data-stu-id="8beee-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="8beee-113">請注意，<xref:System.Windows.Forms.Button>控制項跨越的第一個和第二個資料列。</span><span class="sxs-lookup"><span data-stu-id="8beee-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="8beee-114">設定<xref:System.Windows.Forms.Button>控制項的**ColumnSpan**屬性**1**。</span><span class="sxs-lookup"><span data-stu-id="8beee-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="8beee-115">請注意，<xref:System.Windows.Forms.Button>控制項將移至第一個資料行，並跨越的第一個和第二個資料列。</span><span class="sxs-lookup"><span data-stu-id="8beee-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8beee-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="8beee-116">See Also</span></span>  
 [<span data-ttu-id="8beee-117">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="8beee-117">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
