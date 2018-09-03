---
title: 如何：在 Windows Form 上建立簡單繫結控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 26bc136ea2b7e5bda4a57c5dad65ec3522efcd3d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484948"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="1bdc5-102">如何：在 Windows Form 上建立簡單繫結控制項</span><span class="sxs-lookup"><span data-stu-id="1bdc5-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="1bdc5-103">具有*簡單繫結*，您可以在控制項中顯示單一資料元素，例如資料集資料表中的資料行值。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="1bdc5-104">您可以簡單繫結控制項的任何屬性的資料值。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bdc5-105">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1bdc5-106">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1bdc5-107">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="1bdc5-108">以簡單繫結控制項</span><span class="sxs-lookup"><span data-stu-id="1bdc5-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="1bdc5-109">連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-109">Connect to a data source.</span></span> <span data-ttu-id="1bdc5-110">如需詳細資訊，請參閱 <<c0> [ 連接到資料來源](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="1bdc5-111">在表單中，選取控制項，並顯示**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="1bdc5-112">依序展開 **(DataBindings)** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="1bdc5-113">最常繫結的屬性會顯示底下 **(DataBindings)** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="1bdc5-114">例如，在大部分的控制項**文字**屬性最常繫結。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="1bdc5-115">如果您想要將屬性繫結不是其中一個常見的繫結的屬性，請按一下**省略符號** 按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 中 **（進階）** 方塊，以顯示**格式化與進階繫結**該控制項屬性的對話方塊中的完整清單。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="1bdc5-116">選取您想要繫結，然後按一下下方的下拉式箭頭的屬性**繫結**。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="1bdc5-117">會顯示可用資料來源清單。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="1bdc5-118">展開您想要繫結的資料來源，直到您找到您要的單一資料項目。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="1bdc5-119">例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="1bdc5-120">按一下要繫結項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="1bdc5-121">如果您正在處理**格式化與進階繫結** 對話方塊中，按一下**確定**返回**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="1bdc5-122">如果您想要繫結控制項的其他屬性，請重複步驟 3 到 7。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1bdc5-123">由於簡單繫結控制項顯示單一資料元素，就經常包含 Windows 表單以簡單繫結控制項中的 瀏覽邏輯。</span><span class="sxs-lookup"><span data-stu-id="1bdc5-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdc5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bdc5-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="1bdc5-125">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="1bdc5-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="1bdc5-126">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1bdc5-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
