---
title: HOW TO：使用設計工具繫結 Windows Forms 控制項和 BindingSource 元件
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: a4f87303954494e8e32d32e68fb3f1244f25680a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011708"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="38497-102">HOW TO：使用設計工具繫結 Windows Forms 控制項和 BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="38497-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="38497-103">您已將控制項新增至您的表單，並判斷您的應用程式的使用者介面之後，您可以將控制項繫結到資料來源，以便在執行階段，使用者可以改變，並將儲存應用程式相關的資料。</span><span class="sxs-lookup"><span data-stu-id="38497-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="38497-104">Windows Form 中的繫結的控制項或一系列的控制項最容易完成使用<xref:System.Windows.Forms.BindingSource>控制項在表單上的控制項與資料來源之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="38497-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="38497-105">在表單上的一個或多個控制項可以繫結至資料;在下列程序中，<xref:System.Windows.Forms.TextBox>控制項所繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="38497-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="38497-106">若要完成此程序，則會假設您將繫結至衍生自資料庫的資料來源。</span><span class="sxs-lookup"><span data-stu-id="38497-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="38497-107">如需有關如何從其他存放區的資料建立資料來源的詳細資訊，請參閱 <<c0> [ 加入新的資料來源](/visualstudio/data-tools/add-new-data-sources)。</span><span class="sxs-lookup"><span data-stu-id="38497-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38497-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="38497-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="38497-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="38497-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="38497-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="38497-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="38497-111">將控制項繫結在設計階段</span><span class="sxs-lookup"><span data-stu-id="38497-111">To bind a control at design time</span></span>  
  
1. <span data-ttu-id="38497-112">拖曳<xref:System.Windows.Forms.TextBox>入表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="38497-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2. <span data-ttu-id="38497-113">在 **屬性**視窗：</span><span class="sxs-lookup"><span data-stu-id="38497-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="38497-114">依序展開 **(DataBindings)** 節點。</span><span class="sxs-lookup"><span data-stu-id="38497-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="38497-115">按一下箭號旁<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="38497-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="38497-116">**DataSource** UI 類型編輯器隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="38497-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="38497-117">如果先前已設定資料來源的專案或表單，它會出現。</span><span class="sxs-lookup"><span data-stu-id="38497-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3. <span data-ttu-id="38497-118">按一下 [新增專案資料來源] 以連接至資料，並建立資料來源。</span><span class="sxs-lookup"><span data-stu-id="38497-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4. <span data-ttu-id="38497-119">在 [資料來源組態精靈] 歡迎頁面上，按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="38497-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5. <span data-ttu-id="38497-120">在 **選擇資料來源類型**頁面上，選取**資料庫**。</span><span class="sxs-lookup"><span data-stu-id="38497-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6. <span data-ttu-id="38497-121">在 **選擇資料連接**頁面上，從可用連線清單中選取資料連接。</span><span class="sxs-lookup"><span data-stu-id="38497-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="38497-122">如果您想要的資料連接不是可用的選取**新的連接**來建立新的資料連接。</span><span class="sxs-lookup"><span data-stu-id="38497-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7. <span data-ttu-id="38497-123">選取  **是，將連接儲存為**應用程式組態檔中儲存的連接字串。</span><span class="sxs-lookup"><span data-stu-id="38497-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8. <span data-ttu-id="38497-124">選取要帶入應用程式中的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="38497-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="38497-125">在此情況下，選取您想要的資料表中的 欄位<xref:System.Windows.Forms.TextBox>來顯示。</span><span class="sxs-lookup"><span data-stu-id="38497-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="38497-126">您可以視需要更換預設資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="38497-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="38497-127">按一下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="38497-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="38497-128">在 [**屬性**] 視窗中，按一下箭號旁<xref:System.Windows.Forms.TextBox.Text%2A>屬性一次。</span><span class="sxs-lookup"><span data-stu-id="38497-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="38497-129">在  **DataSource** UI 類型編輯器中，選取要繫結的欄位名稱<xref:System.Windows.Forms.TextBox>到。</span><span class="sxs-lookup"><span data-stu-id="38497-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="38497-130">**DataSource** UI 類型編輯器關閉和資料集，<xref:System.Windows.Forms.BindingSource>和資料表配接器的特定資料連接會加入至您的表單。</span><span class="sxs-lookup"><span data-stu-id="38497-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38497-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38497-131">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="38497-132">新增資料來源</span><span class="sxs-lookup"><span data-stu-id="38497-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="38497-133">[資料來源視窗](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="38497-133">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>