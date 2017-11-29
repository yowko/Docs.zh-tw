---
title: "FontDialog 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1e00fc074148ddd53885bafbb490a3e3868fc0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="c6ee3-102">FontDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="c6ee3-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="c6ee3-103">Windows Form<xref:System.Windows.Forms.FontDialog>元件是預先設定的對話方塊，這是標準的 Windows**字型**對話方塊用來公開目前安裝在系統的字型。</span><span class="sxs-lookup"><span data-stu-id="c6ee3-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="c6ee3-104">使用 Windows 架構應用程式做為簡單的解決方案內它就不需設定您自己的對話方塊中的字型選項。</span><span class="sxs-lookup"><span data-stu-id="c6ee3-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="c6ee3-105">根據預設，對話方塊會顯示清單方塊的字型、 字型樣式和大小。刪除線及底線; 等效果的核取方塊下拉式清單，如指令碼。和字型會如何出現的範例。</span><span class="sxs-lookup"><span data-stu-id="c6ee3-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="c6ee3-106">（指令碼指不同的字元可供指定之字型的指令碼，例如希伯來文或日文）。若要顯示 [字型] 對話方塊，請呼叫<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c6ee3-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="c6ee3-107">索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="c6ee3-107">Key Properties</span></span>  
 <span data-ttu-id="c6ee3-108">此元件的許多設定外觀屬性。</span><span class="sxs-lookup"><span data-stu-id="c6ee3-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="c6ee3-109">設定對話方塊中選取的屬性是<xref:System.Windows.Forms.FontDialog.Font%2A>和<xref:System.Windows.Forms.FontDialog.Color%2A>。</span><span class="sxs-lookup"><span data-stu-id="c6ee3-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="c6ee3-110"><xref:System.Windows.Forms.FontDialog.Font%2A>屬性會設定字型、 樣式、 大小、 指令碼，以及影響; 例如， `Arial, 10pt, style=Italic, Strikeout`。</span><span class="sxs-lookup"><span data-stu-id="c6ee3-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ee3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6ee3-111">See Also</span></span>  
 <xref:System.Windows.Forms.FontDialog>  
 [<span data-ttu-id="c6ee3-112">FontDialog 元件</span><span class="sxs-lookup"><span data-stu-id="c6ee3-112">FontDialog Component</span></span>](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
