---
title: 使用設計工具將控制項系結到 BindingSource 元件
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 35b3fb7b9884f07dd6e2aef311a01d3090c44227
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744386"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="8ca11-102">如何：使用設計工具將 Windows Form 控制項和 BindingSource 元件加以繫結</span><span class="sxs-lookup"><span data-stu-id="8ca11-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="8ca11-103">將控制項新增至表單並決定應用程式的使用者介面之後，您可以將控制項系結至資料來源，以便在執行時間，使用者可以改變和儲存與應用程式相關的資料。</span><span class="sxs-lookup"><span data-stu-id="8ca11-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>

 <span data-ttu-id="8ca11-104">在 Windows Forms 中系結控制項或控制項的系列，最容易使用 <xref:System.Windows.Forms.BindingSource> 控制項做為表單上的控制項和資料來源之間的橋樑來完成。</span><span class="sxs-lookup"><span data-stu-id="8ca11-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>

 <span data-ttu-id="8ca11-105">表單上的一或多個控制項可以系結至資料;在下列程式中，<xref:System.Windows.Forms.TextBox> 控制項系結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="8ca11-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>

 <span data-ttu-id="8ca11-106">若要完成此程式，假設您將系結至衍生自資料庫的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8ca11-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="8ca11-107">如需從其他資料存放區建立資料來源的詳細資訊，請參閱[加入新的資料來源](/visualstudio/data-tools/add-new-data-sources)。</span><span class="sxs-lookup"><span data-stu-id="8ca11-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>

## <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="8ca11-108">若要在設計階段系結控制項</span><span class="sxs-lookup"><span data-stu-id="8ca11-108">To bind a control at design time</span></span>

1. <span data-ttu-id="8ca11-109">將 <xref:System.Windows.Forms.TextBox> 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="8ca11-109">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>

2. <span data-ttu-id="8ca11-110">在 [**屬性**] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="8ca11-110">In the **Properties** window:</span></span>

    1. <span data-ttu-id="8ca11-111">展開 [ **（** 系結）] 節點。</span><span class="sxs-lookup"><span data-stu-id="8ca11-111">Expand the **(DataBindings)** node.</span></span>

    2. <span data-ttu-id="8ca11-112">按一下 [<xref:System.Windows.Forms.TextBox.Text%2A>] 屬性旁的箭號。</span><span class="sxs-lookup"><span data-stu-id="8ca11-112">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

         <span data-ttu-id="8ca11-113">[ **DataSource** UI 類型編輯器] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="8ca11-113">The **DataSource** UI type editor opens.</span></span>

         <span data-ttu-id="8ca11-114">如果先前已設定專案或表單的資料來源，就會出現。</span><span class="sxs-lookup"><span data-stu-id="8ca11-114">If a data source has previously been configured for the project or form, it will appear.</span></span>

3. <span data-ttu-id="8ca11-115">按一下 [新增專案資料來源] 以連接至資料，並建立資料來源。</span><span class="sxs-lookup"><span data-stu-id="8ca11-115">Click **Add Project Data Source** to connect to data and create a data source.</span></span>

4. <span data-ttu-id="8ca11-116">在 [資料來源組態精靈] 歡迎頁面上，按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="8ca11-116">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>

5. <span data-ttu-id="8ca11-117">在 [**選擇資料來源類型**] 頁面上，選取 [**資料庫**]。</span><span class="sxs-lookup"><span data-stu-id="8ca11-117">On the **Choose a Data Source Type** page, select **Database**.</span></span>

6. <span data-ttu-id="8ca11-118">在 [**選擇您的資料連線**] 頁面上，從可用的連接清單中選取資料連線。</span><span class="sxs-lookup"><span data-stu-id="8ca11-118">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="8ca11-119">如果您想要的資料連線無法使用，請選取 [**新增連接**] 來建立新的資料連線。</span><span class="sxs-lookup"><span data-stu-id="8ca11-119">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>

7. <span data-ttu-id="8ca11-120">選取 [**是，儲存連接]，** 將連接字串儲存在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="8ca11-120">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>

8. <span data-ttu-id="8ca11-121">選取要帶入應用程式中的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="8ca11-121">Select the database objects to bring into your application.</span></span> <span data-ttu-id="8ca11-122">在此情況下，請在資料表中選取您想要 <xref:System.Windows.Forms.TextBox> 顯示的欄位。</span><span class="sxs-lookup"><span data-stu-id="8ca11-122">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>

9. <span data-ttu-id="8ca11-123">您可以視需要更換預設資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="8ca11-123">Replace the default dataset name if you want.</span></span>

10. <span data-ttu-id="8ca11-124">按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="8ca11-124">Click **Finish**.</span></span>

11. <span data-ttu-id="8ca11-125">在 [**屬性**] 視窗中，再次按一下 [<xref:System.Windows.Forms.TextBox.Text%2A>] 屬性旁的箭號。</span><span class="sxs-lookup"><span data-stu-id="8ca11-125">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="8ca11-126">在 [ **DataSource** UI 類型編輯器] 中，選取要系結 <xref:System.Windows.Forms.TextBox> 的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="8ca11-126">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>

     <span data-ttu-id="8ca11-127">[ **DataSource** UI 類型編輯器] 隨即關閉，並將該資料連線特定的資料集、<xref:System.Windows.Forms.BindingSource> 和資料表介面卡新增至您的表單。</span><span class="sxs-lookup"><span data-stu-id="8ca11-127">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ca11-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ca11-128">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="8ca11-129">新增資料來源</span><span class="sxs-lookup"><span data-stu-id="8ca11-129">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="8ca11-130">[[資料來源] 視窗](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8ca11-130">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>
