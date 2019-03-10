---
title: HOW TO：調整 Windows Form 的大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 9399069ad5365b025fe8c92b2f10c36c4666f4b4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705412"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="d8b69-102">HOW TO：調整 Windows Form 的大小</span><span class="sxs-lookup"><span data-stu-id="d8b69-102">How to: Resize Windows Forms</span></span>
<span data-ttu-id="d8b69-103">您可以使用幾種方式來指定 Windows Form 的大小。</span><span class="sxs-lookup"><span data-stu-id="d8b69-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="d8b69-104">您可以為 <xref:System.Windows.Forms.Form.Size%2A> 屬性設定新值，或個別調整 <xref:System.Windows.Forms.Control.Height%2A> 或 <xref:System.Windows.Forms.Control.Width%2A> 屬性，以程式設計方式來變更表單的高度和寬度。</span><span class="sxs-lookup"><span data-stu-id="d8b69-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="d8b69-105">如果您使用 Visual Studio，您可以變更使用 Windows Form 設計工具的大小。</span><span class="sxs-lookup"><span data-stu-id="d8b69-105">If you are using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="d8b69-106">另請參閱[How to:調整 Windows Form 使用設計工具的大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d8b69-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>  
  
### <a name="to-resize-a-form-programmatically"></a><span data-ttu-id="d8b69-107">以程式設計方式調整表單的大小</span><span class="sxs-lookup"><span data-stu-id="d8b69-107">To resize a form programmatically</span></span>  
  
-   <span data-ttu-id="d8b69-108">設定表單的 <xref:System.Windows.Forms.Form.Size%2A> 屬性，在執行階段定義表單的大小。</span><span class="sxs-lookup"><span data-stu-id="d8b69-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>  
  
     <span data-ttu-id="d8b69-109">下列程式碼範例示範將表單大小設定為 100 × 100 像素。</span><span class="sxs-lookup"><span data-stu-id="d8b69-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a><span data-ttu-id="d8b69-110">以程式設計方式變更表單寬度和高度</span><span class="sxs-lookup"><span data-stu-id="d8b69-110">To change form width and height programmatically</span></span>  
  
-   <span data-ttu-id="d8b69-111">定義 <xref:System.Windows.Forms.Form.Size%2A> 之後，使用 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 屬性來變更表單高度或寬度。</span><span class="sxs-lookup"><span data-stu-id="d8b69-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="d8b69-112">下列程式碼範例示範將表單的寬度設定為 300 像素 (從表單的左邊緣算起)，而高度則維持不變。</span><span class="sxs-lookup"><span data-stu-id="d8b69-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     <span data-ttu-id="d8b69-113">-或-</span><span class="sxs-lookup"><span data-stu-id="d8b69-113">-or-</span></span>  
  
     <span data-ttu-id="d8b69-114">設定 <xref:System.Windows.Forms.Form.Size%2A> 屬性來變更 <xref:System.Drawing.Size.Width%2A> 或 <xref:System.Drawing.Size.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="d8b69-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>  
  
     <span data-ttu-id="d8b69-115">不過，如下列程式碼範例所示，這種方法比直接設定 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 屬性更困難。</span><span class="sxs-lookup"><span data-stu-id="d8b69-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a><span data-ttu-id="d8b69-116">以程式設計方式遞增變更表單大小</span><span class="sxs-lookup"><span data-stu-id="d8b69-116">To change form size by increments programmatically</span></span>  
  
-   <span data-ttu-id="d8b69-117">若要遞增表單的大小，請設定 <xref:System.Drawing.Size.Width%2A> 和 <xref:System.Drawing.Size.Height%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b69-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="d8b69-118">下列程式碼範例示範將表單的寬度設定為比目前設定還要寬 200 像素。</span><span class="sxs-lookup"><span data-stu-id="d8b69-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="d8b69-119">除非您透過將 <xref:System.Windows.Forms.Form.Size%2A> 屬性設定為新的 <xref:System.Drawing.Size> 結構，來同時設定高度和寬度維度，否則請一律使用 <xref:System.Drawing.Size.Height%2A> 或 <xref:System.Drawing.Size.Width%2A> 屬性來變更表單的維度。</span><span class="sxs-lookup"><span data-stu-id="d8b69-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="d8b69-120"><xref:System.Windows.Forms.Form.Size%2A> 屬性會傳回實值類型的 <xref:System.Drawing.Size> 結構。</span><span class="sxs-lookup"><span data-stu-id="d8b69-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="d8b69-121">您無法指派新值給實值類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b69-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="d8b69-122">因此，下列程式碼範例將無法進行編譯。</span><span class="sxs-lookup"><span data-stu-id="d8b69-122">Therefore, the following code example will not compile.</span></span>  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d8b69-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8b69-123">See also</span></span>
- [<span data-ttu-id="d8b69-124">Windows Forms 使用者入門</span><span class="sxs-lookup"><span data-stu-id="d8b69-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="d8b69-125">增強 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="d8b69-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
