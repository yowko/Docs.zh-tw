---
title: 相
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: c95888f31bfc867e9c028d53072ab3d710256708
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734671"
---
# <a name="windows-forms-coordinates"></a><span data-ttu-id="7ca38-102">Windows Form 座標</span><span class="sxs-lookup"><span data-stu-id="7ca38-102">Windows Forms Coordinates</span></span>
<span data-ttu-id="7ca38-103">Windows Form 的座標系統是以裝置座標為基礎，而在 Windows Forms 中繪製時的基本測量單位是裝置單位（通常是圖元）。</span><span class="sxs-lookup"><span data-stu-id="7ca38-103">The coordinate system for a Windows Form is based on device coordinates, and the basic unit of measure when drawing in Windows Forms is the device unit (typically, the pixel).</span></span> <span data-ttu-id="7ca38-104">螢幕上的點是由 x 和 y 座標配對所描述，而 x 座標則是靠右遞增，而 y 座標則是從上到下遞增。</span><span class="sxs-lookup"><span data-stu-id="7ca38-104">Points on the screen are described by x- and y-coordinate pairs, with the x-coordinates increasing to the right and the y-coordinates increasing from top to bottom.</span></span> <span data-ttu-id="7ca38-105">相對於螢幕的原點位置會根據您指定的是畫面或用戶端座標而有所不同。</span><span class="sxs-lookup"><span data-stu-id="7ca38-105">The location of the origin, relative to the screen, will vary depending on whether you are specifying screen or client coordinates.</span></span>  
  
## <a name="screen-coordinates"></a><span data-ttu-id="7ca38-106">螢幕座標</span><span class="sxs-lookup"><span data-stu-id="7ca38-106">Screen Coordinates</span></span>  
 <span data-ttu-id="7ca38-107">Windows Forms 應用程式會以螢幕座標指定視窗在螢幕上的位置。</span><span class="sxs-lookup"><span data-stu-id="7ca38-107">A Windows Forms application specifies the position of a window on the screen in screen coordinates.</span></span> <span data-ttu-id="7ca38-108">針對螢幕座標，原點是螢幕的左上角。</span><span class="sxs-lookup"><span data-stu-id="7ca38-108">For screen coordinates, the origin is the upper-left corner of the screen.</span></span> <span data-ttu-id="7ca38-109">視窗的完整位置通常是由包含兩個點之螢幕座標（定義視窗的左上角和右下角）的 <xref:System.Drawing.Rectangle> 結構所描述。</span><span class="sxs-lookup"><span data-stu-id="7ca38-109">The full position of a window is often described by a <xref:System.Drawing.Rectangle> structure containing the screen coordinates of two points that define the upper-left and lower-right corners of the window.</span></span>  
  
## <a name="client-coordinates"></a><span data-ttu-id="7ca38-110">用戶端座標</span><span class="sxs-lookup"><span data-stu-id="7ca38-110">Client Coordinates</span></span>  
 <span data-ttu-id="7ca38-111">Windows Forms 應用程式會使用用戶端座標指定表單或控制項中的點位置。</span><span class="sxs-lookup"><span data-stu-id="7ca38-111">A Windows Forms application specifies the position of points in a form or control using client coordinates.</span></span> <span data-ttu-id="7ca38-112">用戶端座標的原點是控制項或表單工作區的左上角。</span><span class="sxs-lookup"><span data-stu-id="7ca38-112">The origin for client coordinates is the upper-left corner of the client area of the control or form.</span></span> <span data-ttu-id="7ca38-113">用戶端座標可確保應用程式在表單或控制項中繪製時，可以使用一致的座標值，不論表單或控制項在螢幕上的位置為何。</span><span class="sxs-lookup"><span data-stu-id="7ca38-113">Client coordinates ensure that an application can use consistent coordinate values while drawing in a form or control, regardless of the position of the form or control on the screen.</span></span>  
  
 <span data-ttu-id="7ca38-114">工作區的維度也會由包含該區域之用戶端座標的 <xref:System.Drawing.Rectangle> 結構所描述。</span><span class="sxs-lookup"><span data-stu-id="7ca38-114">The dimensions of the client area are also described by a <xref:System.Drawing.Rectangle> structure that contains client coordinates for the area.</span></span> <span data-ttu-id="7ca38-115">在所有情況下，矩形的左上角座標會包含在工作區中，而在右下方的座標則會排除。</span><span class="sxs-lookup"><span data-stu-id="7ca38-115">In all cases, the upper-left coordinate of the rectangle is included in the client area, while the lower-right coordinate is excluded.</span></span> <span data-ttu-id="7ca38-116">圖形作業不包含工作區的右和下邊緣。</span><span class="sxs-lookup"><span data-stu-id="7ca38-116">Graphics operations do not include the right and lower edges of a client area.</span></span> <span data-ttu-id="7ca38-117">例如，<xref:System.Drawing.Graphics.FillRectangle%2A> 方法會填滿指定矩形的右邊和下邊緣，但不會包含這些邊緣。</span><span class="sxs-lookup"><span data-stu-id="7ca38-117">For example the <xref:System.Drawing.Graphics.FillRectangle%2A> method will fill up to the right and lower edge of the specified rectangle, but will not include these edges.</span></span>  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a><span data-ttu-id="7ca38-118">從一個座標類型對應到另一個</span><span class="sxs-lookup"><span data-stu-id="7ca38-118">Mapping From One Type of Coordinate to Another</span></span>  
 <span data-ttu-id="7ca38-119">有時候，您可能需要從螢幕座標組應到用戶端座標。</span><span class="sxs-lookup"><span data-stu-id="7ca38-119">Occasionally, you may need to map from screen coordinates to client coordinates.</span></span> <span data-ttu-id="7ca38-120">您可以使用 <xref:System.Windows.Forms.Control> 類別提供的 <xref:System.Windows.Forms.Control.PointToClient%2A> 和 <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法，輕鬆完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="7ca38-120">You can easily accomplish this by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available in the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="7ca38-121">例如，<xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.MousePosition%2A> 屬性會以螢幕座標回報，但您可能會想要將這些內容轉換成用戶端座標。</span><span class="sxs-lookup"><span data-stu-id="7ca38-121">For example, the <xref:System.Windows.Forms.Control.MousePosition%2A> property of <xref:System.Windows.Forms.Control> is reported in screen coordinates, but you may want to convert these to client coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca38-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ca38-122">See also</span></span>

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
