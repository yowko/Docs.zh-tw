---
title: Windows Form 座標
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: 6feabadff17538f4a7368c348f7b72226e2d678e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116128"
---
# <a name="windows-forms-coordinates"></a><span data-ttu-id="442ae-102">Windows Form 座標</span><span class="sxs-lookup"><span data-stu-id="442ae-102">Windows Forms Coordinates</span></span>
<span data-ttu-id="442ae-103">在 Windows Form 座標系統根據裝置座標和量值在 Windows Form 中描繪時的基本單位是裝置單位 （一般而言，像素）。</span><span class="sxs-lookup"><span data-stu-id="442ae-103">The coordinate system for a Windows Form is based on device coordinates, and the basic unit of measure when drawing in Windows Forms is the device unit (typically, the pixel).</span></span> <span data-ttu-id="442ae-104">在螢幕上的點的 x 和 y 座標組說明增加到右並增加從上往下 y 座標的 x 座標。</span><span class="sxs-lookup"><span data-stu-id="442ae-104">Points on the screen are described by x- and y-coordinate pairs, with the x-coordinates increasing to the right and the y-coordinates increasing from top to bottom.</span></span> <span data-ttu-id="442ae-105">相對於畫面中，原點的位置會因您指定螢幕或用戶端座標。</span><span class="sxs-lookup"><span data-stu-id="442ae-105">The location of the origin, relative to the screen, will vary depending on whether you are specifying screen or client coordinates.</span></span>  
  
## <a name="screen-coordinates"></a><span data-ttu-id="442ae-106">螢幕座標</span><span class="sxs-lookup"><span data-stu-id="442ae-106">Screen Coordinates</span></span>  
 <span data-ttu-id="442ae-107">在 Windows Forms 應用程式在螢幕座標的畫面上，指定視窗的位置。</span><span class="sxs-lookup"><span data-stu-id="442ae-107">A Windows Forms application specifies the position of a window on the screen in screen coordinates.</span></span> <span data-ttu-id="442ae-108">螢幕座標，原點是畫面的左上角。</span><span class="sxs-lookup"><span data-stu-id="442ae-108">For screen coordinates, the origin is the upper-left corner of the screen.</span></span> <span data-ttu-id="442ae-109">完整視窗的位置，通常藉由描述<xref:System.Drawing.Rectangle>結構，其中包含定義視窗的左上角和右下角邊角的兩個點的螢幕座標。</span><span class="sxs-lookup"><span data-stu-id="442ae-109">The full position of a window is often described by a <xref:System.Drawing.Rectangle> structure containing the screen coordinates of two points that define the upper-left and lower-right corners of the window.</span></span>  
  
## <a name="client-coordinates"></a><span data-ttu-id="442ae-110">工作區座標</span><span class="sxs-lookup"><span data-stu-id="442ae-110">Client Coordinates</span></span>  
 <span data-ttu-id="442ae-111">在 Windows Forms 應用程式在表單或控制項使用用戶端座標指定點的位置。</span><span class="sxs-lookup"><span data-stu-id="442ae-111">A Windows Forms application specifies the position of points in a form or control using client coordinates.</span></span> <span data-ttu-id="442ae-112">工作區座標中的來源是控制項或表單的工作區的左上角。</span><span class="sxs-lookup"><span data-stu-id="442ae-112">The origin for client coordinates is the upper-left corner of the client area of the control or form.</span></span> <span data-ttu-id="442ae-113">用戶端座標可確保應用程式表單或控制項，不論表單或螢幕上的控制項的位置中繪製時可以使用一致的座標值。</span><span class="sxs-lookup"><span data-stu-id="442ae-113">Client coordinates ensure that an application can use consistent coordinate values while drawing in a form or control, regardless of the position of the form or control on the screen.</span></span>  
  
 <span data-ttu-id="442ae-114">用戶端區域的維度也會描述<xref:System.Drawing.Rectangle>結構，包含區域的座標。</span><span class="sxs-lookup"><span data-stu-id="442ae-114">The dimensions of the client area are also described by a <xref:System.Drawing.Rectangle> structure that contains client coordinates for the area.</span></span> <span data-ttu-id="442ae-115">在所有情況下，矩形的左上角座標包含在工作區中，雖然已排除的右下座標。</span><span class="sxs-lookup"><span data-stu-id="442ae-115">In all cases, the upper-left coordinate of the rectangle is included in the client area, while the lower-right coordinate is excluded.</span></span> <span data-ttu-id="442ae-116">圖形作業不會包含右和下邊緣的工作區。</span><span class="sxs-lookup"><span data-stu-id="442ae-116">Graphics operations do not include the right and lower edges of a client area.</span></span> <span data-ttu-id="442ae-117">例如<xref:System.Drawing.Graphics.FillRectangle%2A>方法會填滿指定的矩形的右邊緣與下緣，但不是包括這些邊緣。</span><span class="sxs-lookup"><span data-stu-id="442ae-117">For example the <xref:System.Drawing.Graphics.FillRectangle%2A> method will fill up to the right and lower edge of the specified rectangle, but will not include these edges.</span></span>  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a><span data-ttu-id="442ae-118">從一種類型的座標對應至另一個</span><span class="sxs-lookup"><span data-stu-id="442ae-118">Mapping From One Type of Coordinate to Another</span></span>  
 <span data-ttu-id="442ae-119">有時候，您可能需要從螢幕座標對應至用戶端座標。</span><span class="sxs-lookup"><span data-stu-id="442ae-119">Occasionally, you may need to map from screen coordinates to client coordinates.</span></span> <span data-ttu-id="442ae-120">您可以使用，輕鬆地完成這<xref:System.Windows.Forms.Control.PointToClient%2A>並<xref:System.Windows.Forms.Control.PointToScreen%2A>方法，可<xref:System.Windows.Forms.Control>類別。</span><span class="sxs-lookup"><span data-stu-id="442ae-120">You can easily accomplish this by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available in the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="442ae-121">比方說，<xref:System.Windows.Forms.Control.MousePosition%2A>屬性<xref:System.Windows.Forms.Control>回報在螢幕座標中，但您可能想要將這些座標轉換。</span><span class="sxs-lookup"><span data-stu-id="442ae-121">For example, the <xref:System.Windows.Forms.Control.MousePosition%2A> property of <xref:System.Windows.Forms.Control> is reported in screen coordinates, but you may want to convert these to client coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442ae-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="442ae-122">See also</span></span>

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
