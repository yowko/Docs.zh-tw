---
title: "如何：為控制項提供透明背景"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5ec2c353a960626c54c05009393bcd80dac1b38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="4cb6f-102">如何：為控制項提供透明背景</span><span class="sxs-lookup"><span data-stu-id="4cb6f-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="4cb6f-103">在舊版 .NET Framework 中，控制項必須先在表單建構函式中設定 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，才能支援設定透明背景色彩。</span><span class="sxs-lookup"><span data-stu-id="4cb6f-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="4cb6f-104">在最新版 Framework 中，您可以在設計階段於 [屬性] <xref:System.Drawing.Color.Transparent%2A>**視窗中，或透過表單建構函式中的程式碼，將大多數控制項的背景色彩設定為** 。</span><span class="sxs-lookup"><span data-stu-id="4cb6f-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cb6f-105">Windows Form 控制項不支援純粹透明。</span><span class="sxs-lookup"><span data-stu-id="4cb6f-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="4cb6f-106">透明的 Windows Form 控制項的背景預設是由其父代所繪製。</span><span class="sxs-lookup"><span data-stu-id="4cb6f-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cb6f-107">即使 <xref:System.Windows.Controls.Button> 屬性設定為 <xref:System.Windows.Forms.ButtonBase.BackColor%2A> ， <xref:System.Drawing.Color.Transparent%2A>控制項也不支援透明背景色彩。</span><span class="sxs-lookup"><span data-stu-id="4cb6f-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="4cb6f-108">為控制項提供透明背景色彩</span><span class="sxs-lookup"><span data-stu-id="4cb6f-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="4cb6f-109">在 [屬性] 視窗中，選擇 <xref:System.Windows.Forms.ButtonBase.BackColor%2A> 屬性並將其設定為 <xref:System.Drawing.Color.Transparent%2A>。</span><span class="sxs-lookup"><span data-stu-id="4cb6f-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb6f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cb6f-110">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="4cb6f-111">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="4cb6f-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="4cb6f-112">使用 Managed 圖形類別</span><span class="sxs-lookup"><span data-stu-id="4cb6f-112">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [<span data-ttu-id="4cb6f-113">操作說明：繪製不透明和半透明線條</span><span class="sxs-lookup"><span data-stu-id="4cb6f-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
