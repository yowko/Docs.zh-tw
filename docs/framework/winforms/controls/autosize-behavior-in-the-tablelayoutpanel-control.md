---
title: AutoSize 在 TableLayoutPanel 控制項中的行為
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: 497991106d151cfe1f3944977828e9c77c27e526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526304"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="b5e6d-102">AutoSize 在 TableLayoutPanel 控制項中的行為</span><span class="sxs-lookup"><span data-stu-id="b5e6d-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="b5e6d-103">相異 AutoSize 行為</span><span class="sxs-lookup"><span data-stu-id="b5e6d-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="b5e6d-104"><xref:System.Windows.Forms.TableLayoutPanel>控制項支援自動調整大小行為如下：</span><span class="sxs-lookup"><span data-stu-id="b5e6d-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="b5e6d-105">透過<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="b5e6d-106">透過<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性<xref:System.Windows.Forms.TableLayoutPanel>控制項的資料行和資料列樣式。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="b5e6d-107">AutoSize 屬性與資料列和資料行樣式</span><span class="sxs-lookup"><span data-stu-id="b5e6d-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="b5e6d-108">下表描述之間的互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性和<xref:System.Windows.Forms.TableLayoutPanel>控制項的資料行和資料列樣式。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="b5e6d-109">自動調整設定</span><span class="sxs-lookup"><span data-stu-id="b5e6d-109">AutoSize setting</span></span>|<span data-ttu-id="b5e6d-110">樣式互動</span><span class="sxs-lookup"><span data-stu-id="b5e6d-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="b5e6d-111"><xref:System.Windows.Forms.TableLayoutPanel>控制會繼續從左到右，與資料行或資料列，或依下列順序配置空間。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="b5e6d-112">1.如果<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性設定為<xref:System.Windows.Forms.SizeType.Absolute>，所指定的像素數<xref:System.Windows.Forms.ColumnStyle.Width%2A>或<xref:System.Windows.Forms.RowStyle.Height%2A>配置。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="b5e6d-113">2.如果<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性設定為<xref:System.Windows.Forms.SizeType.AutoSize>，傳回的子控制項的像素數<xref:System.Windows.Forms.Control.GetPreferredSize%2A>配置方法。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="b5e6d-114">3.之後的所有空間<xref:System.Windows.Forms.SizeType.Absolute>和<xref:System.Windows.Forms.SizeType.AutoSize>資料行或資料列配置時，任何資料行或資料列<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>設<xref:System.Windows.Forms.SizeType.Percent>會用來按比例配置剩餘的可用空間</span><span class="sxs-lookup"><span data-stu-id="b5e6d-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="b5e6d-115">類似於先前的互動，發生例外狀況，<xref:System.Windows.Forms.SizeType.Percent>資料行或資料列取得自動調整大小的長寬。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="b5e6d-116"><xref:System.Windows.Forms.TableLayoutPanel>控制展開的資料行或資料列，以建立足夠的可用空間，讓任何資料行或資料列與<xref:System.Windows.Forms.SizeType.Percent>樣式裁剪其內容。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="b5e6d-117"><xref:System.Windows.Forms.TableLayoutPanel>控制項配置的新空間等比例地根據<xref:System.Windows.Forms.ColumnStyle.Width%2A>或<xref:System.Windows.Forms.RowStyle.Height%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b5e6d-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5e6d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5e6d-118">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="b5e6d-119">TableLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b5e6d-119">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
