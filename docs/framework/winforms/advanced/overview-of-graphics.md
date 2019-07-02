---
title: 圖形概觀
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505330"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="62c10-102">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="62c10-102">Overview of Graphics</span></span>
<span data-ttu-id="62c10-103">GDI + 是應用程式開發介面 (API) 構成的 Microsoft Windows 作業系統的子系統。</span><span class="sxs-lookup"><span data-stu-id="62c10-103">GDI+ is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> <span data-ttu-id="62c10-104">GDI + 會負責顯示螢幕和印表機上的資訊。</span><span class="sxs-lookup"><span data-stu-id="62c10-104">GDI+ is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="62c10-105">正如其名，GDI + 是 GDI，隨附於舊版的 Windows 繪圖裝置介面的後續版本。</span><span class="sxs-lookup"><span data-stu-id="62c10-105">As its name suggests, GDI+ is the successor to GDI, the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="62c10-106">Managed 類別介面</span><span class="sxs-lookup"><span data-stu-id="62c10-106">Managed Class Interface</span></span>  
 <span data-ttu-id="62c10-107">GDI + API 會透過一組部署為 managed 程式碼的類別公開。</span><span class="sxs-lookup"><span data-stu-id="62c10-107">The GDI+ API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="62c10-108">這組類別稱為*managed 的類別介面*GDI +。</span><span class="sxs-lookup"><span data-stu-id="62c10-108">This set of classes is called the *managed class interface* to GDI+.</span></span> <span data-ttu-id="62c10-109">下列命名空間組成 Managed 類別介面：</span><span class="sxs-lookup"><span data-stu-id="62c10-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="62c10-110">圖形裝置介面，例如 GDI + 中，您可以顯示資訊的螢幕或印表機上而不須關心特定顯示裝置的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="62c10-110">With a Graphics Device Interface, such as GDI+, you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="62c10-111">程式設計師會呼叫 GDI + 類別所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="62c10-111">The programmer makes calls to methods provided by GDI+ classes.</span></span> <span data-ttu-id="62c10-112">這些方法接著會適當地呼叫特定裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="62c10-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> <span data-ttu-id="62c10-113">GDI + 隔離應用程式會從圖形硬體。</span><span class="sxs-lookup"><span data-stu-id="62c10-113">GDI+ insulates the application from the graphics hardware.</span></span> <span data-ttu-id="62c10-114">這是此隔離會讓程式設計人員能夠建立與裝置無關的應用程式。</span><span class="sxs-lookup"><span data-stu-id="62c10-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c10-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62c10-115">See also</span></span>

- [<span data-ttu-id="62c10-116">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="62c10-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
