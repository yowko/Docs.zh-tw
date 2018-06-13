---
title: 如何：在執行階段期間隱藏控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
ms.openlocfilehash: 51e804c7f01b55ed7504837042b6c32bf47d9405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532408"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="97b40-102">如何：在執行階段期間隱藏控制項</span><span class="sxs-lookup"><span data-stu-id="97b40-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="97b40-103">但有些的時候，當您可能想要建立使用者控制項在執行階段不可見。</span><span class="sxs-lookup"><span data-stu-id="97b40-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="97b40-104">例如，鬧鐘控制項可能不可見，除了當警示已響起。</span><span class="sxs-lookup"><span data-stu-id="97b40-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="97b40-105">輕鬆達成設定<xref:System.Windows.Forms.Control.Visible%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="97b40-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="97b40-106">如果<xref:System.Windows.Forms.Control.Visible%2A>屬性是`true`，控制項將顯示為一般。</span><span class="sxs-lookup"><span data-stu-id="97b40-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="97b40-107">如果`false`，將隱藏控制項。</span><span class="sxs-lookup"><span data-stu-id="97b40-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="97b40-108">雖然在隱藏時，仍可執行程式碼，在控制項中的，您無法透過使用者介面控制項互動。</span><span class="sxs-lookup"><span data-stu-id="97b40-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="97b40-109">如果您想要建立不可見的控制項仍然會回應使用者輸入 （例如滑鼠點按動作），您應該建立透明的控制項。</span><span class="sxs-lookup"><span data-stu-id="97b40-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="97b40-110">如需詳細資訊，請參閱[為您的控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)。</span><span class="sxs-lookup"><span data-stu-id="97b40-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="97b40-111">若要在執行階段隱藏控制項</span><span class="sxs-lookup"><span data-stu-id="97b40-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="97b40-112">將 <xref:System.Windows.Forms.Control.Visible%2A> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="97b40-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97b40-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97b40-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="97b40-114">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="97b40-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="97b40-115">操作說明：為控制項提供透明背景</span><span class="sxs-lookup"><span data-stu-id="97b40-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
