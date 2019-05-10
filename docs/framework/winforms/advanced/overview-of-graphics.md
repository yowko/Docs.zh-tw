---
title: 圖形概觀
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: 927fc327d9ad42cd3a99af207d04efbc520df8b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645707"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="167d2-102">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="167d2-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="167d2-103">是應用程式開發介面 (API) 構成的 Microsoft Windows 作業系統的子系統。</span><span class="sxs-lookup"><span data-stu-id="167d2-103">is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="167d2-104">負責顯示螢幕和印表機上的資訊。</span><span class="sxs-lookup"><span data-stu-id="167d2-104">is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="167d2-105">正如其名， [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 是 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 的後置項，該繪圖裝置介面包含在舊版 Windows 中。</span><span class="sxs-lookup"><span data-stu-id="167d2-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="167d2-106">Managed 類別介面</span><span class="sxs-lookup"><span data-stu-id="167d2-106">Managed Class Interface</span></span>  
 <span data-ttu-id="167d2-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API 透過一組部署為 managed 程式碼的類別。</span><span class="sxs-lookup"><span data-stu-id="167d2-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="167d2-108">這組類別稱為*managed 的類別介面*至[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="167d2-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="167d2-109">下列命名空間組成 Managed 類別介面：</span><span class="sxs-lookup"><span data-stu-id="167d2-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="167d2-110">圖形裝置介面，例如[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以在螢幕或印表機上顯示資訊，而不須關心特定顯示裝置的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="167d2-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="167d2-111">程式設計師會呼叫 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 類別所提供的方法。</span><span class="sxs-lookup"><span data-stu-id="167d2-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="167d2-112">這些方法接著會適當地呼叫特定裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="167d2-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="167d2-113">會從圖形硬體隔離應用程式。</span><span class="sxs-lookup"><span data-stu-id="167d2-113">insulates the application from the graphics hardware.</span></span> <span data-ttu-id="167d2-114">這是此隔離會讓程式設計人員能夠建立與裝置無關的應用程式。</span><span class="sxs-lookup"><span data-stu-id="167d2-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167d2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="167d2-115">See also</span></span>

- [<span data-ttu-id="167d2-116">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="167d2-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
