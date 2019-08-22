---
title: 使用 WPF 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5ea92b24a2ca30c0ad137d83c8f521a952ad0c6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658492"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="14bf6-102">在 Windows Forms 應用程式中使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="14bf6-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="14bf6-103">您可以在 Windows Forms 架構的應用程式中使用 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="14bf6-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="14bf6-104">雖然這些是兩個不同的視圖技術, 但它們可以順暢地互通。</span><span class="sxs-lookup"><span data-stu-id="14bf6-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="14bf6-105">Visual Studio 中的 Windows Form 設計工具提供用於裝載 Windows Presentation Foundation 控制項的視覺化設計環境。</span><span class="sxs-lookup"><span data-stu-id="14bf6-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="14bf6-106">WPF 控制項是由名為<xref:System.Windows.Forms.Integration.ElementHost>的特殊 Windows Forms 控制項所主控。</span><span class="sxs-lookup"><span data-stu-id="14bf6-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="14bf6-107">這個控制項可讓 WPF 控制項參與表單的版面配置, 並接收鍵盤和滑鼠訊息。</span><span class="sxs-lookup"><span data-stu-id="14bf6-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="14bf6-108">在設計階段, 您可以排列<xref:System.Windows.Forms.Integration.ElementHost>控制項, 就像是任何 Windows Forms 控制項一樣。</span><span class="sxs-lookup"><span data-stu-id="14bf6-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="14bf6-109">您也可以在以 WPF 為基礎的應用程式中使用 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="14bf6-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="14bf6-110">如需詳細資訊, 請參閱[在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="14bf6-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="14bf6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14bf6-111">See also</span></span>

- [<span data-ttu-id="14bf6-112">WPF 和 Windows Forms 交互操作</span><span class="sxs-lookup"><span data-stu-id="14bf6-112">WPF and Windows Forms interoperation</span></span>](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)
