---
title: 如何：為控制項提供工具箱點陣圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 3698d2fdbd0375d0a154d6ecea3a248b31da2aeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537517"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="6852e-102">如何：為控制項提供工具箱點陣圖</span><span class="sxs-lookup"><span data-stu-id="6852e-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="6852e-103">如果您想要有特殊的圖示，為您的控制項出現在**工具箱**，您可以指定特定的映像使用<xref:System.Drawing.ToolboxBitmapAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6852e-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="6852e-104">此類別是一個「屬性」，一種您可以附加至其他類別的特殊類別。</span><span class="sxs-lookup"><span data-stu-id="6852e-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="6852e-105">如需屬性的詳細資訊，請參閱[不在組建： 在 Visual Basic 屬性概觀](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f)適用於 Visual Basic 和[屬性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)Visual C#。</span><span class="sxs-lookup"><span data-stu-id="6852e-105">For more information about attributes, see [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f) for Visual Basic and [Attributes](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) for Visual C#.</span></span>  
  
 <span data-ttu-id="6852e-106">使用<xref:System.Drawing.ToolboxBitmapAttribute>，您可以指定表示 16 x 16 像素點陣圖的路徑和檔案名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="6852e-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="6852e-107">將此點陣圖新增至 [工具箱]，它會接著出現在您的控制項旁邊。</span><span class="sxs-lookup"><span data-stu-id="6852e-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="6852e-108">您也可以指定<xref:System.Type>，在此情況下會載入與這個類型相關聯的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="6852e-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="6852e-109">如果您同時指定<xref:System.Type>和字串，控制項搜尋影像資源字串中的參數包含所指定之類型的組件所指定的名稱與<xref:System.Type>參數。</span><span class="sxs-lookup"><span data-stu-id="6852e-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="6852e-110">指定控制項的工具箱點陣圖</span><span class="sxs-lookup"><span data-stu-id="6852e-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="6852e-111">新增<xref:System.Drawing.ToolboxBitmapAttribute>至類別宣告之前控制項的`Class`適用於 visual Basic 和上述類別宣告中的 Visual C# 中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6852e-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
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
  
2.  <span data-ttu-id="6852e-112">重建專案。</span><span class="sxs-lookup"><span data-stu-id="6852e-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6852e-113">點陣圖並不會針對自動產生的控制項和元件出現在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="6852e-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="6852e-114">若要查看點陣圖，請使用 [選擇工具箱項目] 對話方塊，重新載入控制項。</span><span class="sxs-lookup"><span data-stu-id="6852e-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="6852e-115">如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。</span><span class="sxs-lookup"><span data-stu-id="6852e-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6852e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6852e-116">See Also</span></span>  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [<span data-ttu-id="6852e-117">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="6852e-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="6852e-118">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="6852e-118">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="6852e-119">屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6852e-119">Attributes (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="6852e-120">屬性</span><span class="sxs-lookup"><span data-stu-id="6852e-120">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
