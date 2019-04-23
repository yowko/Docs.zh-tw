---
title: HOW TO：將沒有使用者介面的控制項新增至 Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: 0768f811653543b3370310ccc0b59890273baf52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330099"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="0f0d6-102">HOW TO：將沒有使用者介面的控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f0d6-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="0f0d6-103">非視覺控制項 （或元件） 提供您的應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="0f0d6-104">不像其他控制項，並不提供給使用者的使用者介面元件，並因此不需要在 Windows Form 設計工具介面上顯示。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="0f0d6-105">當元件加入至表單時，Windows Form 設計工具會顯示可調整大小的紙匣底端的表單，其中會顯示所有元件。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="0f0d6-106">控制項新增至元件匣之後, 您可以選取的元件，並設定其屬性，如同任何其他控制項在表單上。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f0d6-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0f0d6-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0f0d6-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="0f0d6-110">若要將元件新增至 Windows 表單</span><span class="sxs-lookup"><span data-stu-id="0f0d6-110">To add a component to a Windows Form</span></span>  
  
1. <span data-ttu-id="0f0d6-111">開啟表單。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-111">Open the form.</span></span> <span data-ttu-id="0f0d6-112">如需詳細資訊，請參閱[如何：在設計工具中顯示 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-112">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="0f0d6-113">在 **工具箱**、 按一下元件，並將它拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="0f0d6-114">您的元件會出現在元件匣中。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="0f0d6-115">此外，元件可以在執行階段新增到表單。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="0f0d6-116">這會是常見的案例中，特別是因為元件並沒有視覺的運算式，不像使用者介面的控制項。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="0f0d6-117">在下列範例中，<xref:System.Windows.Forms.Timer>元件會在執行階段加入。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="0f0d6-118">(請注意，Visual Studio 包含幾個不同的計時器的; 在此案例中，使用 Windows Form<xref:System.Windows.Forms.Timer>元件。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-118">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="0f0d6-119">如需在 Visual Studio 中的不同計時器的詳細資訊，請參閱[伺服器為基礎的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。)</span><span class="sxs-lookup"><span data-stu-id="0f0d6-119">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0f0d6-120">元件通常具有必須設定元件能有效運作的控制項特定屬性。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="0f0d6-121">若是<xref:System.Windows.Forms.Timer>元件下方，設定`Interval`屬性。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="0f0d6-122">請務必，將元件新增至您的專案，，您設定必要的屬性，該元件時。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="0f0d6-123">若要以程式設計方式將元件新增至 Windows 表單</span><span class="sxs-lookup"><span data-stu-id="0f0d6-123">To add a component to a Windows Form programmatically</span></span>  
  
1. <span data-ttu-id="0f0d6-124">建立的執行個體<xref:System.Windows.Forms.Timer>在程式碼中的類別。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2. <span data-ttu-id="0f0d6-125">設定`Interval`屬性來判斷計時器的刻度之間的時間。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3. <span data-ttu-id="0f0d6-126">設定其他任何必要屬性，為您的元件。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="0f0d6-127">下列程式碼顯示如何建立<xref:System.Windows.Forms.Timer>具有其`Interval`屬性集。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0f0d6-128">藉由參考惡意的使用者控制項，您可能會公開本機電腦透過網路的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="0f0d6-129">這只會在惡意人士建立破壞性的自訂控制項，且您不小心將它新增至您的專案的情況下需要考量。</span><span class="sxs-lookup"><span data-stu-id="0f0d6-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0d6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f0d6-130">See also</span></span>

- [<span data-ttu-id="0f0d6-131">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="0f0d6-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="0f0d6-132">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f0d6-132">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="0f0d6-133">如何：將 ActiveX 控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f0d6-133">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="0f0d6-134">如何：Windows Form 之間複製控制項</span><span class="sxs-lookup"><span data-stu-id="0f0d6-134">How to: Copy Controls Between Windows Forms</span></span>](how-to-copy-controls-between-windows-forms.md)
- [<span data-ttu-id="0f0d6-135">將控制項加入 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f0d6-135">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="0f0d6-136">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="0f0d6-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="0f0d6-137">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="0f0d6-137">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="0f0d6-138">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="0f0d6-138">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
