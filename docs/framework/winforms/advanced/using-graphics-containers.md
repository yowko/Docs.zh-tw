---
title: "使用圖形容器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 244f8e8a280369798daf12f8a61519826f937a4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-graphics-containers"></a><span data-ttu-id="9c9d6-102">使用圖形容器</span><span class="sxs-lookup"><span data-stu-id="9c9d6-102">Using Graphics Containers</span></span>
<span data-ttu-id="9c9d6-103">A<xref:System.Drawing.Graphics>物件提供方法，例如<xref:System.Drawing.Graphics.DrawLine%2A>， <xref:System.Drawing.Graphics.DrawImage%2A>，和<xref:System.Drawing.Graphics.DrawString%2A>向量影像、 點陣影像和文字顯示。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="9c9d6-104">A<xref:System.Drawing.Graphics>物件也有影響的品質和方向的項目所繪製的數個屬性。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="9c9d6-105">比方說，平滑化的模式屬性會決定是否反鋸齒功能會套用至的直線和曲線，並全局轉換屬性會影響的位置和旋轉繪製的項目。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="9c9d6-106">A<xref:System.Drawing.Graphics>物件都與特定顯示裝置。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="9c9d6-107">當您使用<xref:System.Drawing.Graphics>物件来繪製在視窗中，<xref:System.Drawing.Graphics>物件也會與該特定視窗相關聯。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="9c9d6-108">A<xref:System.Drawing.Graphics>物件可以視為容器因為它包含一組會影響繪圖的屬性，它會連結至裝置的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="9c9d6-109">您可以建立第二個容器內的現有<xref:System.Drawing.Graphics>藉由呼叫物件<xref:System.Drawing.Graphics.BeginContainer%2A>方法，<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c9d6-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="9c9d6-110">In This Section</span></span>  
 [<span data-ttu-id="9c9d6-111">管理圖形物件的狀態</span><span class="sxs-lookup"><span data-stu-id="9c9d6-111">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="9c9d6-112">描述如何管理品質設定、 裁剪區域和轉換<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="9c9d6-113">使用巢狀圖形容器</span><span class="sxs-lookup"><span data-stu-id="9c9d6-113">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 <span data-ttu-id="9c9d6-114">示範如何使用容器來控制的狀態<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="9c9d6-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
