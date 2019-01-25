---
title: HOW TO：建立具有影像的按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: cfebe53047531ecddde42a3a0596dfd949629ecd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682046"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="e0c9c-102">HOW TO：建立具有影像的按鈕</span><span class="sxs-lookup"><span data-stu-id="e0c9c-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="e0c9c-103">此範例示範如何在包含影像<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0c9c-104">範例</span><span class="sxs-lookup"><span data-stu-id="e0c9c-104">Example</span></span>  
 <span data-ttu-id="e0c9c-105">下列範例會建立兩個<xref:System.Windows.Controls.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="e0c9c-106">一個<xref:System.Windows.Controls.Button>包含文字，另一個映像。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="e0c9c-107">映像位於稱為資料，也就是此範例的專案資料夾的子資料夾的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="e0c9c-108">當使用者按一下<xref:System.Windows.Controls.Button>有映像、 背景和其他文字<xref:System.Windows.Controls.Button>變更。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="e0c9c-109">這個範例會建立<xref:System.Windows.Controls.Button>藉由使用標記來控制，但會使用程式碼撰寫<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e0c9c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0c9c-110">See also</span></span>
- [<span data-ttu-id="e0c9c-111">控制項</span><span class="sxs-lookup"><span data-stu-id="e0c9c-111">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="e0c9c-112">控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="e0c9c-112">Control Library</span></span>](../../../../docs/framework/wpf/controls/control-library.md)
