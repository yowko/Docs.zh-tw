---
title: HOW TO：提供控制項的工具箱點陣圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 428af7e4396fde8ac29046d73adda95dbe2182f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910477"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="bd075-102">HOW TO：提供控制項的工具箱點陣圖</span><span class="sxs-lookup"><span data-stu-id="bd075-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="bd075-103">如果您想要讓控制項的特殊圖示出現在 [**工具箱**] 中, 您可以使用<xref:System.Drawing.ToolboxBitmapAttribute>來指定特定的影像。</span><span class="sxs-lookup"><span data-stu-id="bd075-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="bd075-104">此類別是一個「屬性」，一種您可以附加至其他類別的特殊類別。</span><span class="sxs-lookup"><span data-stu-id="bd075-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="bd075-105">如需屬性的詳細資訊, 請參閱的C#Visual Basic 或[屬性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)的[屬性總覽 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) 。</span><span class="sxs-lookup"><span data-stu-id="bd075-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="bd075-106"><xref:System.Drawing.ToolboxBitmapAttribute>使用, 您可以指定字串, 指出 16 x 16 圖元點陣圖的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="bd075-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="bd075-107">將此點陣圖新增至 [工具箱]，它會接著出現在您的控制項旁邊。</span><span class="sxs-lookup"><span data-stu-id="bd075-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="bd075-108">您也可以指定<xref:System.Type>, 在此情況下, 會載入與該類型相關聯的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="bd075-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="bd075-109">如果您同時<xref:System.Type>指定和字串, 控制項會在包含<xref:System.Type>參數所指定之類型的元件中, 搜尋具有 string 參數所指定之名稱的影像資源。</span><span class="sxs-lookup"><span data-stu-id="bd075-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="bd075-110">指定控制項的工具箱點陣圖</span><span class="sxs-lookup"><span data-stu-id="bd075-110">To specify a Toolbox bitmap for your control</span></span>  
  
1. <span data-ttu-id="bd075-111">在 visual Basic 的`Class`關鍵字之前以及 visual C#的類別宣告上方, 將加入至控制項的類別宣告。<xref:System.Drawing.ToolboxBitmapAttribute></span><span class="sxs-lookup"><span data-stu-id="bd075-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2. <span data-ttu-id="bd075-112">重建專案。</span><span class="sxs-lookup"><span data-stu-id="bd075-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bd075-113">點陣圖並不會針對自動產生的控制項和元件出現在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="bd075-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="bd075-114">若要查看點陣圖，請使用 [選擇工具箱項目] 對話方塊，重新載入控制項。</span><span class="sxs-lookup"><span data-stu-id="bd075-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="bd075-115">如需詳細資訊，請參閱[逐步解說：自動將自訂群組件](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)填入工具箱。</span><span class="sxs-lookup"><span data-stu-id="bd075-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd075-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd075-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="bd075-117">逐步解說：使用自訂群組件自動填入工具箱</span><span class="sxs-lookup"><span data-stu-id="bd075-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="bd075-118">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="bd075-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="bd075-119">屬性概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd075-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="bd075-120">屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd075-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
