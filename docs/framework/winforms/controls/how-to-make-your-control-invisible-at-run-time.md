---
title: HOW TO：在執行階段隱藏控制項
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
ms.openlocfilehash: e9af529541a40a951d6defea180dbbef04c8f3be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913701"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="aafec-102">HOW TO：在執行階段隱藏控制項</span><span class="sxs-lookup"><span data-stu-id="aafec-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="aafec-103">有些的時候您可能想要建立在執行階段不會察覺的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="aafec-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="aafec-104">例如，警示時鐘控制項可能除了警示已響起時不可見。</span><span class="sxs-lookup"><span data-stu-id="aafec-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="aafec-105">這可以輕鬆地藉由設定<xref:System.Windows.Forms.Control.Visible%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="aafec-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="aafec-106">如果<xref:System.Windows.Forms.Control.Visible%2A>屬性是`true`，您的控制項將會出現如往常。</span><span class="sxs-lookup"><span data-stu-id="aafec-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="aafec-107">如果`false`，將隱藏控制項。</span><span class="sxs-lookup"><span data-stu-id="aafec-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="aafec-108">雖然在控制項中的程式碼仍可能在隱藏時執行，但是您不能透過使用者介面控制項互動。</span><span class="sxs-lookup"><span data-stu-id="aafec-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="aafec-109">如果您想要建立不可見的控制項，仍會回應使用者輸入 （例如滑鼠點按），您應該建立透明的控制項。</span><span class="sxs-lookup"><span data-stu-id="aafec-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="aafec-110">如需詳細資訊，請參閱 <<c0> [ 為您的控制項提供透明背景](how-to-give-your-control-a-transparent-background.md)。</span><span class="sxs-lookup"><span data-stu-id="aafec-110">For more information, see [Giving Your Control a Transparent Background](how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="aafec-111">若要在執行階段隱藏控制項</span><span class="sxs-lookup"><span data-stu-id="aafec-111">To make your control invisible at run time</span></span>  
  
1. <span data-ttu-id="aafec-112">將 <xref:System.Windows.Forms.Control.Visible%2A> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="aafec-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aafec-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aafec-113">See also</span></span>

- <xref:System.Windows.Forms.Control.Visible%2A>
- [<span data-ttu-id="aafec-114">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="aafec-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="aafec-115">如何：為控制項提供透明背景</span><span class="sxs-lookup"><span data-stu-id="aafec-115">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)
