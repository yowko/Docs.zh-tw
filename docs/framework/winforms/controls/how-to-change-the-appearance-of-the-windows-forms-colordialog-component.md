---
title: "如何：變更 Windows Form ColorDialog 元件的外觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11edb1019b8fedde368d712ab27dd0954a2de50a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="c13eb-102">如何：變更 Windows Form ColorDialog 元件的外觀</span><span class="sxs-lookup"><span data-stu-id="c13eb-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="c13eb-103">您可以設定 Windows Form 的外觀<xref:System.Windows.Forms.ColorDialog>元件使用其屬性的數目。</span><span class="sxs-lookup"><span data-stu-id="c13eb-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="c13eb-104">此對話方塊包含兩個區段，其中顯示基本色彩，可讓使用者定義自訂色彩的其中一個。</span><span class="sxs-lookup"><span data-stu-id="c13eb-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="c13eb-105">大部分的屬性會限制哪些使用者可以從對話方塊中選取的色彩。</span><span class="sxs-lookup"><span data-stu-id="c13eb-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="c13eb-106">如果<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>屬性設定為`true`，允許使用者定義自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="c13eb-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="c13eb-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A>屬性是`true`如果對話方塊中展開為定義自訂色彩; 否則，使用者必須按一下 」 定義自訂色彩 」 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c13eb-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="c13eb-108">當<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>屬性設定為`true`，對話方塊中顯示基本色彩集中的所有可用色彩。</span><span class="sxs-lookup"><span data-stu-id="c13eb-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="c13eb-109">如果<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>屬性設定為`true`，使用者無法選取遞色的色彩，則只有純色可用來選取。</span><span class="sxs-lookup"><span data-stu-id="c13eb-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="c13eb-110">如果<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>屬性設定為`true`，說明 按鈕會出現在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="c13eb-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="c13eb-111">當使用者按一下 [說明] 按鈕，<xref:System.Windows.Forms.ColorDialog>元件的<xref:System.Windows.Forms.CommonDialog.HelpRequest>就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="c13eb-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="c13eb-112">若要設定 [色彩] 對話方塊的外觀</span><span class="sxs-lookup"><span data-stu-id="c13eb-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="c13eb-113">設定<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>， <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>， <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>，和<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>所需值的屬性。</span><span class="sxs-lookup"><span data-stu-id="c13eb-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c13eb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c13eb-114">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="c13eb-115">ColorDialog 元件</span><span class="sxs-lookup"><span data-stu-id="c13eb-115">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="c13eb-116">ColorDialog 元件概觀</span><span class="sxs-lookup"><span data-stu-id="c13eb-116">ColorDialog Component Overview</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
